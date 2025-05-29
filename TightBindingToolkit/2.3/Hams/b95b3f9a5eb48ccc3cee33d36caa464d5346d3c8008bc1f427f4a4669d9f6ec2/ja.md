```julia
FullHamiltonian(uc::UnitCell, bz::BZ) --> Matrix{Matrix{ComplexF64}}
```

`BZ`内のすべての運動量点での完全ハミルトニアンを返し、`UnitCell`に存在する結合に対応します。
