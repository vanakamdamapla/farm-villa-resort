# Google Drive Integration & Setup Guide

This guide explains how to host your villa's configuration and images on Google Drive so your single-page website can load them dynamically.

---

## 1. Preparing and Uploading `data.json`

1. Open the [data.json](file:///C:/Users/Admin/.gemini/antigravity/scratch/luxury-villa-website/data.json) file included in this folder.
2. Edit the prices, discounts, contact details, dates, and testimonials to match your villa's current status.
3. Save the file.
4. Go to [Google Drive](https://drive.google.com) and upload the `data.json` file.

---

## 2. Making Files Public on Google Drive

For the website to fetch your data, the files must be accessible to anyone:
1. Right-click on the uploaded `data.json` in Google Drive.
2. Click **Share** -> **Share**.
3. Under *General access*, click the dropdown and change it from **Restricted** to **Anyone with the link**.
4. Set the role to **Viewer**.
5. Click **Done**.

*Follow these exact same steps for any images you upload to Google Drive for your gallery.*

---

## 3. Formatting Direct Download URLs

Google Drive sharing links look like this:
`https://drive.google.com/file/d/FILE_ID/view?usp=sharing`

To use them on your website, you need the **direct download URL**. Copy the `FILE_ID` from the link (the long string between `/d/` and `/view`) and format it as follows:

### For the `data.json` configuration file:
Use this format:
`https://docs.google.com/uc?export=download&id=FILE_ID`

*Example:*
`https://docs.google.com/uc?export=download&id=1a2B3c4D5e6F7g8H9i0J`

### For Images in the `gallery.images` list:
Use the Google User Content format (recommended for reliability and performance):
`https://lh3.googleusercontent.com/d/FILE_ID`

*Example:*
`https://lh3.googleusercontent.com/d/1a2B3c4D5e6F7g8H9i0J`

*Note: You can also use standard public web URLs (like Unsplash, Imgur, or direct links from your hosting provider) in the image list if you prefer not to use Google Drive.*

---

## 4. Updating the Website Configuration

Once you have your public `data.json` direct link:
1. Open [index.html](file:///C:/Users/Admin/.gemini/antigravity/scratch/luxury-villa-website/index.html) in a text editor.
2. Find the constant `CONFIG_URL` near the top of the script tag (around line 20-30):
   ```javascript
   const CONFIG_URL = 'https://docs.google.com/uc?export=download&id=YOUR_FILE_ID';
   ```
3. Replace `'YOUR_FILE_ID'` with your actual Google Drive file ID.
4. Save the file. Your website is now fully synchronized with your Google Drive spreadsheet/configuration!

---

## 5. Walkthrough Videos

You can use direct video links, YouTube, or Vimeo links in the `videos` array:
- **YouTube:** E.g., `https://www.youtube.com/watch?v=VIDEO_ID` or `https://youtu.be/VIDEO_ID` (the code automatically converts these to embed formats).
- **Vimeo:** E.g., `https://vimeo.com/VIDEO_ID` (automatically converted).
- **Direct Video Links:** E.g., `https://example.com/walkthrough.mp4` (rendered using HTML5 `<video>` tag).
