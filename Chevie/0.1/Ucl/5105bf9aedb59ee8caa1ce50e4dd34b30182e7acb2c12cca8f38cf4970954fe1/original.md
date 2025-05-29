`XTable(uc;classes=false)`

This  function presents  in a  different way  the information obtained from `ICCTable`. Let $X̃_{u,ϕ}=q^{1/2(codim C-dim Z(𝐋 ))}X_{u,ϕ}$ where `C` is the  class of `u` and `Z(𝐋 )` is the center of Levi subgroup on which lives the cuspidal local system attached to the local system `(u,ϕ)`.

Then  `XTable(uc)` gives the decomposition of the functions $X̃_{u,ϕ}$ on local   systems.  `t=XTable(uc,classes==true)`  gives  the  values  of  the functions   $X̃_{u,ϕ}$   on   unipotent   classes.   A   side  effect  of `classes=true`  is  to  compute  the  cardinal  of  the unipotent conjugacy classes,  available in `t.cardClass`; in this case displaying `t` will show the  cardinal  of  the  centralizers  of  unipotent  elements, available in `t.centClass`.

```julia-repl
julia> W=coxgroup(:G,2)
G₂

julia> XTable(UnipotentClasses(W))
Values of character sheaves X̃ᵪ on local systems φ
┌──────────┬───────────────────────────────────────────┐
│X̃ᵪ|φ      │   1 A₁ Ã₁ G₂(a₁)⁽¹¹¹⁾ G₂(a₁)⁽²¹⁾ G₂(a₁) G₂│
├──────────┼───────────────────────────────────────────┤
│X_φ₁‚₀^G₂ │   1  1  1           .          .      1  1│
│X_φ₁‚₆^G₂ │  q⁶  .  .           .          .      .  .│
│X_φ′₁‚₃^G₂│  q³  .  q           .          q      .  .│
│X_φ″₁‚₃^G₂│  q³ q³  .           .          .      .  .│
│X_φ₂‚₁^G₂ │ qΦ₈  q  q           .          .      q  .│
│X_φ₂‚₂^G₂ │q²Φ₄ q² q²           .          .      .  .│
│X_Id^.    │   .  .  .          q²          .      .  .│
└──────────┴───────────────────────────────────────────┘
```

The functions `X̃` in the first column are decorated by putting as an exponent the relative groups $W_𝐆 (𝐋)$.

```julia-repl
julia> t=XTable(UnipotentClasses(W);classes=true)
Values of character sheaves X̃ᵪ on unipotent classes
┌──────────┬─────────────────────────────────────────────────────────┐
│X̃ᵪ|class  │           1     A₁     Ã₁ G₂(a₁) G₂(a₁)₍₂₁₎ G₂(a₁)₍₃₎ G₂│
├──────────┼─────────────────────────────────────────────────────────┤
│X_φ₁‚₀^G₂ │           1      1      1      1          1         1  1│
│X_φ₁‚₆^G₂ │          q⁶      .      .      .          .         .  .│
│X_φ′₁‚₃^G₂│          q³      .      q     2q          .        -q  .│
│X_φ″₁‚₃^G₂│          q³     q³      .      .          .         .  .│
│X_φ₂‚₁^G₂ │         qΦ₈      q      q      q          q         q  .│
│X_φ₂‚₂^G₂ │        q²Φ₄     q²     q²      .          .         .  .│
│X_Id^.    │           .      .      .     q²        -q²        q²  .│
├──────────┼─────────────────────────────────────────────────────────┤
│|C_𝐆(u)|  │q⁶Φ₁²Φ₂²Φ₃Φ₆ q⁶Φ₁Φ₂ q⁴Φ₁Φ₂    6q⁴        2q⁴       3q⁴ q²│
└──────────┴─────────────────────────────────────────────────────────┘

julia> XTable(UnipotentClasses(W,2))
Values of character sheaves X̃ᵪ on local systems φ
┌──────────┬──────────────────────────────────────────────────┐
│X̃ᵪ|φ      │   1 A₁ Ã₁ G₂(a₁)⁽¹¹¹⁾ G₂(a₁)⁽²¹⁾ G₂(a₁) G₂⁽¹¹⁾ G₂│
├──────────┼──────────────────────────────────────────────────┤
│X_φ₁‚₀^G₂ │   1  1  1           .          .      1      .  1│
│X_φ₁‚₆^G₂ │  q⁶  .  .           .          .      .      .  .│
│X_φ′₁‚₃^G₂│  q³  .  q           .          q      .      .  .│
│X_φ″₁‚₃^G₂│  q³ q³  .           .          .      .      .  .│
│X_φ₂‚₁^G₂ │ qΦ₈  q  q           .          .      q      .  .│
│X_φ₂‚₂^G₂ │q²Φ₄ q² q²           .          .      .      .  .│
│X_Id^.    │   .  .  .          q²          .      .      .  .│
│X_Id^.    │   .  .  .           .          .      .      q  .│
└──────────┴──────────────────────────────────────────────────┘

julia> XTable(UnipotentClasses(rootdatum(:sl,4)))
Values of character sheaves X̃ᵪ on local systems φ
┌────────┬────────────────────────────────────────────┐
│X̃ᵪ|φ    │1111 211 22⁽¹¹⁾ 22 31 4 4^(ζ₄) 4⁽⁻¹⁾ 4^(ζ₄³)│
├────────┼────────────────────────────────────────────┤
│X₁₁₁₁^A₃│  q⁶   .      .  .  . .      .     .       .│
│X₂₁₁^A₃ │q³Φ₃  q³      .  .  . .      .     .       .│
│X₂₂^A₃  │q²Φ₄  q²      . q²  . .      .     .       .│
│X₃₁^A₃  │ qΦ₃ qΦ₂      .  q  q .      .     .       .│
│X₄^A₃   │   1   1      .  1  1 1      .     .       .│
│X₁₁^A₁  │   .   .     q³  .  . .      .     .       .│
│X₂^A₁   │   .   .     q²  .  . .      .     q       .│
│X_Id^.  │   .   .      .  .  . .   q³⁄₂     .       .│
│X_Id^.  │   .   .      .  .  . .      .     .    q³⁄₂│
└────────┴────────────────────────────────────────────┘
```
