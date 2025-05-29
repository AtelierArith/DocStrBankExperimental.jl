```
compute_value(gfa::GlobalFunctionApproximator, v::AbstractVector)
```

グローバル関数近似器に基づいて、クエリポイント v での関数の値を返します。

```
compute_value(gfa::GlobalFunctionApproximator, v_list::AbstractVector{V}) where V <: AbstractVector{Float64}
```

グローバル関数近似器に基づいて、クエリポイントのリストに対する関数の値を返します。
