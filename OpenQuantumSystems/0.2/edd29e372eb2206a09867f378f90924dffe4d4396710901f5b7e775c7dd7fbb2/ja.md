```
tracenorm(rho)
```

`rho`のトレースノルム。これは次のように定義されます。

$$
T(ρ) = \operatorname{tr}\{\sqrt{ρ^† ρ}\}.
$$

`rho`がエルミートかどうかに応じて、[`tracenorm_h`](@ref)または[`tracenorm_nh`](@ref)が呼び出されます。
