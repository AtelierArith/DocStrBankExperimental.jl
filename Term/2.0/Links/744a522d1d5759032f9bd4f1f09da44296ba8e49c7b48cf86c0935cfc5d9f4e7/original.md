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

Custom constructor to make a `RenderableText` out of a `Link`, specialized to take into account `Link`'s different sizes  between displayed and actual text.
