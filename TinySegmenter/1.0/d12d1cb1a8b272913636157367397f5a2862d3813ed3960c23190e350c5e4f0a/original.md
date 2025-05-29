```
tokenize(text::AbstractString)
```

Given a `text` string, `tokenize` attempts to segment it into a list of words, and in particular tries to segment Japanese text into words ("tokens" or "segments"), using the TinySegmenter algorithm. It returns an array of substrings consisting of the guessed tokens in `text`, in the order that they appear.
