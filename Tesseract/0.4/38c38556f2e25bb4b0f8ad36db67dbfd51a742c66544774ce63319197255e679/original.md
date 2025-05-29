```
tess_lstm_box(
    inst::TessInst,
    page::Integer = Int32(1)
)::Union{String, Nothing}
```

Return the UTF-8 box file for LSTM training.  If there is an error 'nothing' is returned.

**Arguments:**

| T   | Name | Default    | Description                     |
|:--- |:---- |:---------- |:------------------------------- |
| R   | inst |            | The Tesseract instance to call. |
| O   | page | `Int32(1)` | The page to get the data for.   |

**Details:**

This method will call `tess_recognize()` if it has not been called yet for the image.

**Example:**

```jldoctest; filter = r"(\s+)"
using Tesseract

download_languages()

instance = TessInst()
pix = sample_pix()

tess_image(instance, pix)
tess_resolution(instance, 72)

box = tess_lstm_box(instance)

for line in split(box, '\n'; keepempty = false)[1:5]
    println(line)
end

# output

N 11 577 422 591 0
o 11 577 422 591 0
  11 577 422 591 0
o 11 577 422 591 0
n 11 577 422 591 0
```

See also: [`tess_unlv`](@ref), [`tess_word_box`](@ref), [`tess_text_box`](@ref)
