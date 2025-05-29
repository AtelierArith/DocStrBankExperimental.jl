```
set_retries(ctx; count=5, all_apis=false)
```

Args:

  * ctx: the context to set the options for

Keyword Args:

  * count: how many times to retry (default 5)
  * all_apis: whether to retry even mutating APIs e.g. `put!` (default false)
