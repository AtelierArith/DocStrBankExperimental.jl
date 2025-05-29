```julia
addhopping!(ftm::FTBModel, R::AbstractVector{Int64}, n::Int64, m::Int64,
    p::Int64, hopping::Number)
```

⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩に`hopping`を追加します。

この関数は、周期的駆動によるオンサイトエネルギーを追加しません。
