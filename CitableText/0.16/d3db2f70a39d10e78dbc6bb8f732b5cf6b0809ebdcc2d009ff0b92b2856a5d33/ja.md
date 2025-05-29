```julia
workcontains(urn1, urn2)

```

`urn1`の作業コンポーネントが`urn2`の作業コンポーネントを含むか、等しい場合は真です。

# 例

```julia-repl
julia>
workcontains(CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1.1")
CtsUrn("urn:cts:greekLit:tlg0012.tlg001:1")
)
```
