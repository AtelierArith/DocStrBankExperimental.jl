```
@inside <expr>
```

セルを除外して効率的なループを自動化するシンプルなマクロです。例えば、

```
@inside p[I] = sum(loc(0,I))
```

は次のようになります。

```
@loop p[I] = sum(loc(0,I)) over I ∈ inside(p)
```

[`@loop`](@ref)を参照してください。
