```
function packaging(setid; extra = [])
```

Return the XML string for the packaging of the item with the given setid. The packaging XML is highly variable in labeling and may be deeply nested, so an array or tuple is not computed, but instead the XML itself is returned.

`extra` is optional. If provided it should be a `Dict` or list of string `Pair`s, and can be "pagesize", "page"
