```
UrlTextCell
```

A text cell that contains a URL and is rendered using the ANSI escape sequence `\e8]`.

!!! warning
    Some terminals **do not** support this feature, leading to a layout problem in the printed table.


# Fields

**Public**

  * `text::String`: The label of the URL.
  * `url::String`: The URL.

**Private**

  * `_crop::Int`: Number of characters in the text that must be cropped when rendering the   URL.
  * `_left_pad::Int`: Number of spaces to be added to the left of the text when rendering the   URL.
  * `_right_pad::Int`: Number of spaces to be added to the right of the text when rendering   the URL.
  * `_suffix::String`: Suffix to be appended to the text when rendering the URL.
