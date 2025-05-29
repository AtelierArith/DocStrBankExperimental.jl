```
silvera_goldman_singlet(r::T) where T<:Real
```

*H2*のシングレット $(^{1}\Sigma_{g}^{+})$ ポテンシャルの *Hartree* a.u. におけるパラメータ化 (Eh = 219474.6 cm-1),

$$
   V_{s}(r)=V_{t}(r)-J(r)
$$

ここで、$V_{t}$ はトリプレットポテンシャル ([`silvera_goldman_triplet`](@ref)) であり、$J(r)$ は交換寄与 ([`silvera_goldman_triplet`](@ref)) です。
