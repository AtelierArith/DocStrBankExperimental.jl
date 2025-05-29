```
struct Tsv
    level::Int
    page::Int
    block::Int
    paragraph::Int
    line::Int
    word::Int
    left::Int
    top::Int
    width::Int
    height::Int
    conf::Float32
    text::String
end
```

This structure holds the details of a line in the TSV formatted text provided by the tesseract library.

**Values:**

| Name      | Description                                                                        |
|:--------- |:---------------------------------------------------------------------------------- |
| level     | Identifies what the line describes.                                                |
| page      | This is the page number passed into the `tess_tsv()` method.                       |
| block     | Identifies the block on the page.                                                  |
| paragraph | The paragraph number in the block.                                                 |
| line      | The line in the paragraph.                                                         |
| word      | The word in the line.                                                              |
| left      | Left edge of the item in pixels.                                                   |
| top       | Top edge of the item in pixels.                                                    |
| width     | Width of the item in pixels.                                                       |
| height    | Height of the item in pixels.                                                      |
| conf      | How confident the OCR engine is of the word (`0` - `100`). `-1` if level is not 5. |
| text      | The word that was decoded from the image.                                          |

**Details:**

Level identifies what information the line is providing:

  * `1` - Page information, added at the start of the page.
  * `2` - Block information, added at the start of a block.
  * `3` - Paragraph information, added at the start of a paragraph.
  * `4` - Line information, added at the start of a line.
  * `5` - Word information, identifies a word that was read from the page.

The left, top, width, and height values define a box in pixels that encompases the item.  So if the level is 1, the box describes the whole image.  If the level is `1`, then the box encloses the block that was extracted, and so on down to the word that was extracted.

See also: [`tess_parsed_tsv`](@ref)
