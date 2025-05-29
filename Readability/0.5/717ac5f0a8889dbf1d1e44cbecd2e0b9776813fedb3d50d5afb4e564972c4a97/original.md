```
coleman_liau(text::String)
```

Returns the Coleman-Liau Index of `text`.

CLI = 0.0588 * L - 0.296 * S - 15.8

L = number of characters per 100 words

S = number of sentences per 100 words

## Argument

  * `text::String`: The text to analyze.

## Returns

  * `Number`: The Coleman-Liau Index.
