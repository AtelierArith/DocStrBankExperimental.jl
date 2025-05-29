```
loc = whereis(sf::StackFrame)
```

Return location information for a single frame of a stack trace. If `sf` corresponds to a frame that was inlined, `loc` will be `nothing`. Otherwise `loc` will be `(filepath, line)`.
