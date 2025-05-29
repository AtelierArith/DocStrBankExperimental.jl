```
report_text(text::AbstractString; jetconfigs...) -> JETToplevelResult
report_text(text::AbstractString, filename::AbstractString; jetconfigs...) -> JETToplevelResult
```

トップレベルの `text` を分析し、型レベルのエラーを返します。
