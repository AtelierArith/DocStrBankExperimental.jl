The TinySegmenter module provides a function `tokenize` to  break a string of Japanese text into an array of substrings representing tokens:

```
using TinySegmenter

join(tokenize("私の名前は中野です"), " | ")
# "私 | の | 名前 | は | 中野 | です"
```
