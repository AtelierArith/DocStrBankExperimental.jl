```
run_tesseract(image, extra_args...; kwargs...) -> String
```

Function to run Tesseract over an image in memory, and get the results in a `String`. Errors / Warnings are reported through `Logging`, so no exceptions are thrown.

# Arguments

  * `image`: Image to be processed, in a format compatible with `Images` module.
  * `extra_args::String...`: Optional arguments to change the nature of the output (e.g, [`"tsv"`](https://tesseract-ocr.github.io/tessdoc/Command-Line-Usage.html))

# Keywords

  * `lang::Union{String, Nothing}` Language to be configured in Tesseract (optional)
  * `psm::Integer`: Page segmentation modes (PSM):

      * `psm=0`:   Orientation and script detection (OSD) only.
      * `psm=1`:   Automatic page segmentation with OSD.
      * `psm=2`:   Automatic page segmentation, but no OSD, or OCR.
      * `psm=3`:   Fully automatic page segmentation, but no OSD. (Default)
      * `psm=4`:   Assume a single column of text of variable sizes.
      * `psm=5`:   Assume a single uniform block of vertically aligned text.
      * `psm=6`:   Assume a single uniform block of text.
      * `psm=7`:   Treat the image as a single text line.
      * `psm=8`:   Treat the image as a single word.
      * `psm=9`:   Treat the image as a single word in a circle.
      * `psm=10`:  Treat the image as a single character.
      * `psm=11`:  Sparse text. Find as much text as possible in no particular order.
      * `psm=12`:  Sparse text with OSD.
      * `psm=13`:  Raw line. Treat the image as a single text line,   bypassing hacks that are Tesseract-specific.
  * `oem::Integer`: OCR Engine modes (OEM):

      * `oem=0`:   Legacy engine only.
      * `oem=1`:   Neural nets LSTM engine only. (Default)
      * `oem=2`:   Legacy + LSTM engines.
      * `oem=3`:   Default, based on what is available.
  * `kwargs`: Other key-value pairs to be sent to Tesseract command as "-c" config variables.   You can check the options with `tesseract --print-parameters`.

# Returns

  * `String`: text extracted, or empty string in case an error occurs

# Examples

```julia-repl
julia> using Images;
julia> using OCReract;
julia> img_path = "/path/to/img.png";
julia> img = load(img_path);
julia> res_text = run_tesseract(img, psm=3, oem=1);
julia> println(strip(res_text));
```
