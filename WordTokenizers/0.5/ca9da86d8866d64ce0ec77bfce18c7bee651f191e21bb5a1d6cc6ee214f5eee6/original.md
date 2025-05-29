```
set_sentence_splitter(fun)
```

Call this to set the default sentence splitter to invoke the passed in function `fun` It will be used by `split_sentences`. Calling this will trigger recompilation of any functions that use `split_sentences`.

Calling `set_sentence_splitter`  will give method overwritten warnings. They are expected, be worried if they do not occur
