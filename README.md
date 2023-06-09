# av-scripts
Collection of bash scripts for audio / video shenanigans. Mostly generated by chatGPT

## chaptermerge
This script combines separate M4B audiobook chapters into a single M4B file, preserving chapter information.

## Requirements

- FFmpeg
- MP4v2-utils (specifically `mp4chaps`)

### Installing Dependencies

#### FFmpeg

- **Ubuntu/Debian**: `sudo apt-get install ffmpeg`
- **macOS (with Homebrew)**: `brew install ffmpeg`

#### MP4v2-utils

- **Ubuntu/Debian**: Build and install from source (see instructions below)
- **macOS (with Homebrew)**: `brew install mp4v2`

##### Building MP4v2-utils from source (Ubuntu/Debian)

1. Install the necessary build tools and dependencies:
```
sudo apt-get update
sudo apt-get install -y build-essential git pkg-config autoconf automake libtool
```

2. Clone the `mp4v2` repository:
```
git clone https://github.com/TechSmith/mp4v2.git
cd mp4v2
```

3. Prepare the build system:
```
autoreconf --install
./configure
```

4. Build and install the `mp4v2-utils` package:
```
make
sudo make install
```

5. Update the shared library cache:
```
sudo ldconfig
```

## Usage

./chaptermerge <input_directory>


- `<input_directory>`: The directory containing the M4B audiobook chapters

The output file will be saved in a subfolder with the same name as the audiobook (determined from the album metadata) in the parent folder of the input directory. The subfolder and output file will be created if they don't exist.

### Example

Assuming you have an audiobook with separate chapter files in a directory called `my_audiobook`, you can run the script as follows:

./chaptermerge my_audiobook

The output file will be saved in a subfolder named after the audiobook within the parent directory of `my_audiobook`.

## Notes

- The script should be run on a Unix-based system (Linux or macOS) or Windows Subsystem for Linux (WSL).
- The script will automatically detect and convert Windows file paths to Unix file paths if needed.
- The script will display the output path in the correct format depending on whether it's a Unix or Windows path.
- Combine with Readarr for a seamless audobook experience!
