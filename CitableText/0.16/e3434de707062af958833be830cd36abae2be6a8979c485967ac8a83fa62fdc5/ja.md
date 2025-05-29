```julia
passagecontains(urn1, urn2)

```

`urn1`のパッセージコンポーネントが`urn2`のパッセージコンポーネントを含むか、等しい場合は真。

# 例

```julia-repl
julia>
passagecontains(CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1.1")
CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1")
)
```
