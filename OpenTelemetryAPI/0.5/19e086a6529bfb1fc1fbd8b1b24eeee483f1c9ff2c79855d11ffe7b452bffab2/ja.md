```
attributes(s::AbstractSpan)
```

[`BoundedAttributes`](@ref) が期待されます。

!!! warning
    返された属性を直接変更しないでください。ユーザーは常に `(s::AbstractSpan)[key]=val` を通じて属性を変更するべきです。なぜなら、最初に `is_recording(s)` をチェックするからです。

