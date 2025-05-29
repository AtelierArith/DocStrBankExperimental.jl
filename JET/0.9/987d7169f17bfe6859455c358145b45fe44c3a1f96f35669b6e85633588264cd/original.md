```
report_text(text::AbstractString; jetconfigs...) -> JETToplevelResult
report_text(text::AbstractString, filename::AbstractString; jetconfigs...) -> JETToplevelResult
```

Analyzes top-level `text` and returns back type-level errors.
