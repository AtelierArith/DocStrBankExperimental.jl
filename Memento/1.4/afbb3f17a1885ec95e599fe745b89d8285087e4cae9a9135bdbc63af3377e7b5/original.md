```
emit{F, O}(handler::DefaultHandler{F ,O}, rec::Record) where {F<:Formatter, O<:IO}
```

Handles printing any `Record` with any `Formatter` and `IO` types.
