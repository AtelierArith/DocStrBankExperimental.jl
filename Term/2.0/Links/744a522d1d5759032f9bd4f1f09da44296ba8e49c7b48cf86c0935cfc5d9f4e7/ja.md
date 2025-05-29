---

```
Renderables.RenderableText(
    link::Link,
    args...;
    style::Union{Nothing,String} = link.style,
    width::Int = link.measure.w,
    background::Union{Nothing,String} = nothing,
    justify::Symbol = :left,
)
```

`Link`の異なるサイズを考慮して、`Link`から`RenderableText`を作成するためのカスタムコンストラクタ。
