```
tracedistance(rho, sigma)
```

`rho`と`sigma`の間のトレース距離。

これは次のように定義されます。

$$
T(ρ,σ) = \frac{1}{2} Tr\{\sqrt{(ρ - σ)^† (ρ - σ)}\}.
$$

これは[`tracenorm`](@ref)を呼び出し、$ρ-σ$がエルミートかどうかに応じて、[`tracenorm_h`](@ref)または[`tracenorm_nh`](@ref)を使用します。
