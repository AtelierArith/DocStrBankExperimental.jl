`Zeros(domainType::Type, dim_in::Tuple, [codomainType::Type,] dim_out::Tuple)`

配列 `x` のサイズ `dim_in` で掛け算を行うと、サイズ `dim_out` のゼロで埋められた配列 `y` を返す `LinearOperator` を作成します。

便利なことに、`Zeros` は任意の `AbstractOperator` から構築できます。

```julia
julia> Zeros(Eye(10,20))
0  ℝ^(10, 20) -> ℝ^(10, 20)

julia> Zeros([Eye(10,20) Eye(10,20)])
[0,0]  ℝ^(10, 20)  ℝ^(10, 20) -> ℝ^(10, 20)
```
