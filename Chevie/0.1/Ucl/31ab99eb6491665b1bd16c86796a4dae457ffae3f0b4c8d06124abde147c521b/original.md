`GreenTable(uc;classes=false)`

Keeping the same notations as in the description of 'XTable', this function returns a table of the functions $Q_{wF}$, attached to elements $wF∈ W_𝐆 (𝐋)⋅F$ where $W_𝐆 (𝐋)$ are the relative weyl groups attached to cuspidal local  systems.  These  functions  are  defined  by $Q_{wF}=∑_{u,ϕ} ϕ̃(wF) X̃_{u,ϕ}$. An point to note is that in the principal Springer series, when `𝐓`  is  a  maximal  torus,  the  function  $Q_{wF}$  coincides  with the Deligne-Lusztig  character $R^𝐆  _{𝐓_W}(1)$. As  for 'XTable', by default the  table  gives  the  values  of  the  functions  on  local  systems.  If `classes=true`  is  given,  then  it  gives  the  values  of  the functions $Q_{wF}$ on conjugacy classes.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> GreenTable(UnipotentClasses(W))
Values of Green functions Q_wF on local systems φ
┌──────────┬──────────────────────────────────────────────────────────┐
│Qᴵ_wF|φ   │        1     A₁       Ã₁ G₂(a₁)⁽¹¹¹⁾ G₂(a₁)⁽²¹⁾ G₂(a₁) G₂│
├──────────┼──────────────────────────────────────────────────────────┤
│Q_A₀^G₂   │  Φ₂²Φ₃Φ₆   Φ₂Φ₃ (2q+1)Φ₂           .          q   2q+1  1│
│Q_Ã₁^G₂   │-Φ₁Φ₂Φ₃Φ₆  -Φ₁Φ₃       Φ₂           .          q      1  1│
│Q_A₁^G₂   │-Φ₁Φ₂Φ₃Φ₆   Φ₂Φ₆      -Φ₁           .         -q      1  1│
│Q_G₂^G₂   │ Φ₁²Φ₂²Φ₃ -Φ₁Φ₂²    -Φ₁Φ₂           .         -q     Φ₂  1│
│Q_A₂^G₂   │ Φ₁²Φ₂²Φ₆  Φ₁²Φ₂    -Φ₁Φ₂           .          q    -Φ₁  1│
│Q_A₁+Ã₁^G₂│  Φ₁²Φ₃Φ₆  -Φ₁Φ₆ (2q-1)Φ₁           .         -q  -2q+1  1│
│Q_^.      │        .      .        .          q²          .      .  .│
└──────────┴──────────────────────────────────────────────────────────┘
```

The  functions $Q_{wF}$ depend only on the conjugacy class of `wF`, so in the  first column the indices of 'Q' are the names of the conjugacy classes of $W_𝐆(𝐋)$. The exponents are the names of the groups $W_𝐆(𝐋)$.

```julia-repl
julia> GreenTable(UnipotentClasses(W);classes=true)
Values of Green functions Q_wF on unipotent classes
┌───────────┬────────────────────────────────────────────────────────┐
│Qᴵ_wF|class│        1     A₁       Ã₁ G₂(a₁) G₂(a₁)₍₂₁₎ G₂(a₁)₍₃₎ G₂│
├───────────┼────────────────────────────────────────────────────────┤
│Q_A₀^G₂    │  Φ₂²Φ₃Φ₆   Φ₂Φ₃ (2q+1)Φ₂   4q+1       2q+1        Φ₂  1│
│Q_Ã₁^G₂    │-Φ₁Φ₂Φ₃Φ₆  -Φ₁Φ₃       Φ₂   2q+1          1       -Φ₁  1│
│Q_A₁^G₂    │-Φ₁Φ₂Φ₃Φ₆   Φ₂Φ₆      -Φ₁  -2q+1          1        Φ₂  1│
│Q_G₂^G₂    │ Φ₁²Φ₂²Φ₃ -Φ₁Φ₂²    -Φ₁Φ₂    -Φ₁         Φ₂      2q+1  1│
│Q_A₂^G₂    │ Φ₁²Φ₂²Φ₆  Φ₁²Φ₂    -Φ₁Φ₂     Φ₂        -Φ₁     -2q+1  1│
│Q_A₁+Ã₁^G₂ │  Φ₁²Φ₃Φ₆  -Φ₁Φ₆ (2q-1)Φ₁  -4q+1      -2q+1       -Φ₁  1│
│Q_^.       │        .      .        .     q²        -q²        q²  .│
└───────────┴────────────────────────────────────────────────────────┘

julia> GreenTable(UnipotentClasses(rootdatum(:sl,4)))
Values of Green functions Q_wF on local systems φ
┌────────┬──────────────────────────────────────────────────────────────────┐
│Qᴵ_wF|φ │     1111          211 22⁽¹¹⁾       22   31 4 4^(ζ₄) 4⁽⁻¹⁾ 4^(ζ₄³)│
├────────┼──────────────────────────────────────────────────────────────────┤
│Q₁₁₁₁^A₃│  Φ₂²Φ₃Φ₄ (3q²+2q+1)Φ₂      . (2q+1)Φ₂ 3q+1 1      .     .       .│
│Q₂₁₁^A₃ │-Φ₁Φ₂Φ₃Φ₄   -q³+q²+q+1      .       Φ₂   Φ₂ 1      .     .       .│
│Q₂₂^A₃  │  Φ₁²Φ₃Φ₄        -Φ₁Φ₄      .  2q²-q+1  -Φ₁ 1      .     .       .│
│Q₃₁^A₃  │ Φ₁²Φ₂²Φ₄        -Φ₁Φ₂      .    -Φ₁Φ₂    1 1      .     .       .│
│Q₄^A₃   │ -Φ₁³Φ₂Φ₃        Φ₁²Φ₂      .      -Φ₁  -Φ₁ 1      .     .       .│
│Q₁₁^A₁  │        .            .   q²Φ₂        .    . .      .     q       .│
│Q₂^A₁   │        .            .  -q²Φ₁        .    . .      .     q       .│
│Q_^.    │        .            .      .        .    . .   q³⁄₂     .       .│
│Q_^.    │        .            .      .        .    . .      .     .    q³⁄₂│
└────────┴──────────────────────────────────────────────────────────────────┘
```
