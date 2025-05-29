```
struct YearString end

YearString(s) -> s

YearString(n::Number) -> year2str(n)
```

This is a type that acts as a converter to ensure year columns are parsed correctly as strings.  If blank given, left blank.
