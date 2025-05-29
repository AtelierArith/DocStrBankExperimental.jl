```julia
sethopping!(ftm::FTBModel, R::AbstractVector{Int64}, n::Int64, m::Int64,
    p::Int64, hopping::Number)
```

⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩をすべてのlに対して`hopping`に設定します。あるいは、`hopping`は⟨n|H(p)|m⟩であり、H(t) = ∑H(p)e^{-ipΩt}です。

フロケ Hamiltonian H*F=H-i∂tは、基底関数|n⟩e^{-ilΩt}において、(H*F)*{l, l-p}=⟨⟨0; n e^{-ilΩt}|H(t)|R; m e^{-i(l-p)Ωt}⟩⟩-δ*{p,0}lΩです。この関数は自動的に上記のδ関数を処理します。
