```
taylorsolve(H::Array{CPType,2}, x::Vector{CPType}, k::Int, t::Real) -> ArrayReg, CPType
```

テイラー切断法を使用してハミルトニアンをシミュレートします。状態レジスタとそれを見つける逆確率を返します。
