```
compute_value(lfa::LocalFunctionApproximator, v::AbstractVector)
```

ローカル関数近似器に基づいて、いくつかのクエリポイントvでの関数の値を返します。

```
compute_value(lfa::LocalFunctionApproximator, v_list::AbstractVector{V}) where V <: AbstractVector{Float64}
```

ローカル関数近似器に基づいて、クエリポイントのリストに対する関数の値を返します。
