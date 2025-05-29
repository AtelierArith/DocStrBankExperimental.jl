```
make_card(list; word_size=12, line_width=8, break_words=false, kwargs...)
```

Make bingo card 

# Arguments

  * `list`: an array containing bingo words

# Keywords

  * `backend=pyplot`: plotting backend.
  * `word_size`: the size of words in points
  * `line_width`: the number of characters per line for each word or phrase
  * `break_words`: break long words when wrapping words
  * `kwargs`: variable keyword arguments to pass to the `plot` function
