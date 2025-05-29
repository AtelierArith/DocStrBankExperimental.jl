```
prompt_char(question::AbstractString, options::Vector{Char},
            default::Union{Char, Nothing}=nothing)
```

インタラクティブに`question`を尋ね、`options`のキーのみを回答として受け付けます。すべてのキーは入力時に小文字に変換されます。`default`がnothingでなく、'RET'が押された場合、`default`が返されます。

'^C'が押されると、InterruptExceptionがスローされます。
