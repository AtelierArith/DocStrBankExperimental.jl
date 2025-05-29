```
RegexDict(::Tuple{Union{Regex, String}, T}...)
```

Creates a dictionary that uses Regexes as keys and tests against those when looking up keys. Symbols can be used as lookup keys, by using their name. If multiple Regexes match a key, the value associated with any of them may be returned.
