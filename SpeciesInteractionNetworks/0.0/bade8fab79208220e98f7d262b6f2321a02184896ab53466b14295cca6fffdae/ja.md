```
swap!(N::SpeciesInteractionNetwork{<:Partiteness, <:Binary}, ::Type{Degree})
```

次数による制約を持つ置換は、相互作用する種のペア (r1, s1) と (r2, s2) を選び、それらを (r1, s2) と (r2, s1) に置き換えようとすることで機能します。
