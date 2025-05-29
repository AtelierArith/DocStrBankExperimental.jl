```
depict(value::Any)::String
```

Depict a `value` in an error message or a log entry. Unlike `"$(value)"`, this focuses on producing a human-readable indication of the type of the value, so it double-quotes strings, prefixes symbols with `:`, and reports the type and sizes of arrays rather than showing their content, as well as having specializations for the various `Daf` data types.
