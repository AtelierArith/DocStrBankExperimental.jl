```
query_selector(page::Page, selector::String) -> Union{Dict, Nothing}
```

Find the first element matching the given selector using DOM.querySelector.

If found, returns the "nodeId" value, otherwise returns nothing.
