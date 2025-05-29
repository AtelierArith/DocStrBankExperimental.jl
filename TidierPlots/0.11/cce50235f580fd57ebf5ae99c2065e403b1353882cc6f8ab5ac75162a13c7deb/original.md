```
label_wrap(width)
```

Wrap text strings to a specified width, breaking at spaces.

# Arguments

  * `width`: The maximum number of characters in a line before wrapping.

# Examples

```julia
labeler = label_wrap(10)
labeler(["This is a long sentence."]) # ["This is a
long
sentence."]
```
