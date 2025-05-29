```
tracenorm(rho)
```

`rho`のトレースノルム。

これは次のように定義されます。

$$
T(ρ) = Tr\{\sqrt{ρ^† ρ}\}.
$$

`rho`がエルミートであるかどうかに応じて、[`tracenorm_h`](@ref)または[`tracenorm_nh`](@ref)が呼び出されます。
