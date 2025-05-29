`standard_parabolic(W,H)`

与えられた反射部分群 `H` またはその単純ルートのインデックスがパラボリックでない場合は `nothing` を返し、そうでない場合は `H^w` が `W` の標準パラボリック部分群であるような `w` を返します。

```julia-repl
julia> W=coxgroup(:E,6)
E₆

julia> R=reflection_subgroup(W,[20,30,19,22])
E₆₍₁‚₉‚₁₉‚₂₀₎=A₄₍₃₁₂₄₎Φ₁²

julia> p=standard_parabolic(W,R)
(1,4,49,12,10)(2,54,62,3,19)(5,17,43,60,9)(6,21,34,36,20)(7,24,45,41,53)(8,65,50,15,22)(11,32,31,27,28)(13,48,46,37,40)(14,51,58,44,29)(16,23,35,33,30)(18,26,39,55,38)(42,57,70,72,56)(47,68,67,63,64)(52,59,71,69,66)

julia> p==standard_parabolic(W,[19,1,9,20]) # can give inclusiongens
true

julia> reflection_subgroup(W,[20,30,19,22].^p) # same as R^p
E₆₍₂₄₅₆₎=A₄Φ₁²

julia> R=reflection_subgroup(W,[1,2,3,5,6,35])
E₆₍₁‚₂‚₃‚₅‚₆‚₃₅₎=A₂₍₁₃₎×A₂₍₂₆₎×A₂₍₄₅₎

julia> standard_parabolic(W,R)
```
