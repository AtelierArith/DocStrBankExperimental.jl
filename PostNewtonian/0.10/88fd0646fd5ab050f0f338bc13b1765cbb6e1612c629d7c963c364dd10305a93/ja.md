```
γₚₙ⁻¹(γ, pnsystem)
inverse_separation_inverse(γ, pnsystem)
```

`γₚₙ(pnsystem) = γ`となるように`v`を返します。`pnsystem`が`v`で評価されるときに。

入力の`pnsystem`における`v`の値は無視されることに注意してください。任意の値を使用できます。また、`PostNewtonian.vindex`を使用して、`pnsystem`内の`v`の値を返された値に設定することが便利であることも知っておくと良いでしょう。

```julia
pnsystem.state[PostNewtonian.vindex] = γₚₙ⁻¹(γ, pnsystem)
```

[`r⁻¹`](@ref)も参照してください。
