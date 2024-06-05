# the `g` is silent.

## what?

A tool to convert your music collection from A to B.
Written for and used by me to convert my FLAC library to ALAC + 256 AAC.

## why?

Historically iTunes/Apple Music has been the preferred way to convert because of Apple's superior encoder. If you run this on macOS / if `aac_at` is available, then this will tool will also use Apple's encoder. You are not sacrificing quality using this.

## quality

This tool is simple and opinionated. I assume you want the best possible (but practical) quality.

- `alac` & `flac`: lossless
- `aac`: 256K w/Apple's encoder (where available)
- `ogg`: libvorbis -q:a 8 which is the edge of human perception
- `wav`: pcm_s16le (should we be doing something different?)
- `mp3`: 320kbps

The `--ipod` flag is a shortcut for 256 AAC since that's typically the best choice for an iPod

## performance

Runs as many threads as your machine; it's very fast. With 10 cores, it's 10x faster than Apple Music at converting ALAC to AAC.

## how?

### requirements

- [ffmpeg](https://ffmpeg.org) must be installed, or at least located locally, such that you can specify with the path with `--ffmpeg` option. Uses your system path by default.
- [node & npm](https://nodejs.org/en) is used to executed and run this tool; they must be installed such that the `npx` command succeeds. You may use [pnpx](https://pnpm.io/installation) instead, if you prefer.

There are no other dependencies.

```sh

npx github:jmonster/music-monstger --input "/path/to/input" --output "/path/to/output" --ipod
```

## options

```sh
node script.js \
  --input <inputDir> \
  --output <outputDir> \
  --codec [flac|alac|aac|wav|mp3|ogg] \
  [--ipod] \
  [--ffmpeg /opt/homebrew/bin/ffmpeg] \
  [--dry-run]
```
