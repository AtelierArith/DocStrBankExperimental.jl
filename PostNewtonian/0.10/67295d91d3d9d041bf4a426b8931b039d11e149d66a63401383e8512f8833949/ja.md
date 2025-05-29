```
r⁻¹(r, pnsystem)
separation_inverse(r, pnsystem)
```

`pnsystem`が`v`で評価されるときに`r = r(v)`となるような`v`を返します。

入力の`pnsystem`における`v`の値は無視されることに注意してください。任意の値を使用できます。また、`PostNewtonian.vindex`を使用して、`pnsystem`内の`v`の値を返された値に設定することが便利であることも知っておくと良いでしょう。

```julia
pnsystem.state[PostNewtonian.vindex] = r⁻¹(r, pnsystem)
```

[`γₚₙ⁻¹`](@ref)も参照してください。
