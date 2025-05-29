```
s = format(unit::Unit; names = false, definition = false)
```

Format the unit `unit` as a string. If names is true, then definition uses the unit names (e.g. meter) instead of symbols (e.g. m). If definition is true, then the unit should be expressed in terms of basic units (m²·kg·s⁻³ instead of W).
