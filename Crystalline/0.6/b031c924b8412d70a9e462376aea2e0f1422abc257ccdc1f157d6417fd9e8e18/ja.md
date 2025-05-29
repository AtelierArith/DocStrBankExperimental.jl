```
@S_str -> SymOperation
```

文字列として与えられた三重項形式から `SymOperation` を構築します。

## 例

```jldoctest
julia> S"-y,x"
4⁺ ──────────────────────────────── (-y,x)
 ┌ 0 -1 ╷ 0 ┐
 └ 1  0 ╵ 0 ┘
```
