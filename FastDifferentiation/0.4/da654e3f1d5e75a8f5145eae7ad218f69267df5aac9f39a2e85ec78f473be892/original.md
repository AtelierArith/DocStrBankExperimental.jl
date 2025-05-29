```
clear_cache()
```

Clears the global expression cache. To maximize efficiency of expressions the differentation system automatically eliminates common subexpressions by checking for their existence in the global expression cache. Over time this cache can become arbitrarily large. Best practice is to clear the cache before you start defining expressions, define your expressions and then clear the cache.
