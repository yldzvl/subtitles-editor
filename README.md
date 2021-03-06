# Subtitles Editor

This editor allows you to make edits to SubRip Text (SRT) files with subtitles - shift the timestamps, do a linear correction, or translate them to another language.

## Features

- Colorizer for SubRip Text (SRT) files.
- Shift all timestamps by a specific time value.
- Renumber frame sequence with specified start index.
- Linear correction by mapping two existing time stamps to new values.
- Translate subtitles to different languages.
- Only subtitles in selection are affected. If there is no selection, all subtitles are affected.

## Usage

Use command **Subtitles: Shift** and enter offset time to shift subtitles. The format is "HH:mm:ss,zzz". You can use negative time if subtitles are too late.

With **Subtitles: Renumber**, you can renumber the frames using the sequence wuth specified start index. After selecting this options, enter the start of the sequence (usually `1`) and it will be renumbered accordingly.

The command **Subtitles: Linear Correction** prompts you for two timestamp mappings. The input is in form "original timestamp -> new timestamp". Pick one point from the beginning of the movie and second one from the end of the movie to get the best approximation.

Use command **Subtitles: Translate** to translate subtitles to another language using Google translation service.

## For Developers

### Updating Supported Languages

The languages that can be used for translation are published by Google in Google documentation. The extension uses languages defined in `src/languages.json` file.

To convert the published table to JSON:

- copy the table from Google documentation (https://cloud.google.com/translate/docs/languages)
- replace `^(.*?)\t(.*?)(?: \(.+\))?$` with `\t"$2": "$1",`
- remove the last comma
- wrap the result in curly braces
- save it as `src/languages.json`

## Release Notes

### 0.0.1

Initial release of Subtitle Editor.

### 1.0.0

Added option to translate subtitles.

### 1.0.1

Added option to renumber the sequence of the frames.
