```
dG_o_dT2s_x_T2s_lorentzian(κ)
```

ローレンツ線形に対応するグリーン関数の導関数を、`κ = (t-τ)/T2s` における `T2s` に関して評価し、それに `T2s` を掛けます。

掛け算は、関数が単に `κ = (t-τ)/T2s` に依存するように追加されています。実際の導関数は `dG_o_dT2s_x_T2s_lorentzian((t-τ)/T2s)/T2s` で与えられます。

# 例

```jldoctest
julia> t = 100e-6;

julia> τ = 0;

julia> T2s = 10e-6;

julia> dGdT2s = dG_o_dT2s_x_T2s_lorentzian((t-τ)/T2s)/T2s
45.39992976248485
```
