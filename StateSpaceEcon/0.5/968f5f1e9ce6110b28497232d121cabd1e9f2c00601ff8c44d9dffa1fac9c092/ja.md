```
zeroarray(model, plan)
```

指定されたモデルとプランに対して、適切な次元の `Matrix{Float64}` を作成します。初期値は0です。

この関数は `Matrix` を返します。 [`zerodata`](@ref) を使用することをお勧めします。これは [`SimData`](@ref) を返します。 [`zeroworkspace`](@ref) も参照してください。

!!! note "非推奨の注意"
    `zeroarray(model, range)` は将来のバージョンで削除されます。常にシミュレーション `Plan` を明示的に作成してください。

