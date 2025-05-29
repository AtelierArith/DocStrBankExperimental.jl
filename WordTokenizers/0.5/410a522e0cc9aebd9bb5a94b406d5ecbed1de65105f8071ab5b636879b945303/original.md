```
set_tokenizer(fun)
```

Call this to set the default tokenizer to invoke the passed in function `fun` It will be used by `tokenize`. Calling this will trigger recompilation of any functions that use `tokenize`.

Calling `set_tokenizer`  will give method overwritten warnings. They are expected, be worried if they do not occur
