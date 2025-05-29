```
decompose(bf::CompositeGTBasisFuncs{T, D}, splitGaussFunc::Bool=false) -> 
Matrix{<:BasisFunc{T, D}}
```

`CompositeGTBasisFuncs`を[`BasisFunc`](@ref)の`Matrix`に分解します。各列の合計は、入力基底関数の1つの軌道を表します。`splitGaussFunc`が`true`の場合、各列は1つの[`GaussFunc`](@ref)のみを持つ`BasisFunc`で構成されます。
