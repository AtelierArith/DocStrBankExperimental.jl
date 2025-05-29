```
dG_o_dT2s_x_T2s_gaussian(κ)
```

ガウス線形に対応するグリーン関数の導関数を、`T2s` に関して `κ = (t-τ)/T2s` で評価し、それを `T2s` で掛け算します。

掛け算は、関数が単に `κ = (t-τ)/T2s` のみに依存するように追加されています。実際の導関数は `dG_o_dT2s_x_T2s_gaussian((t-τ)/T2s)/T2s` で与えられます。

# 例

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> dGdT2s = dG_o_dT2s_x_T2s_gaussian((t-τ)/T2s)/T2s
1.9287498479639177e-15
```
