# 拡張ヘルプ

```
is_interior_point(v::AbstractVector{<:Real}, X::LazySet; [kwargs]...)
```

### アルゴリズム

デフォルトの実装は、誤差許容範囲 `ε` を用いて `v ∈ interior(X)` を判断します。これは、中心が `v` で半径が `ε` のノルム `p` の `Ballp` が `X` に含まれているかどうかをチェックすることによって行われます。
