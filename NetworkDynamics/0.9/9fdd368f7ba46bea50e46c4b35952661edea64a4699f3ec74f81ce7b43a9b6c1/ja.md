```
SymbolicView{N,VT} <: AbstractVetor{VT}
```

は、名前付き次元を持つ（小さめの）固定サイズベクトル型です。その主な目的は、[`ComponentCondition`](@ref) および [`ComponentAffect`](@ref) 関数内で変数に名前付きでアクセスできるようにすることです。

つまり、`ComponentAffect` が `sym=[:x, :y]` と宣言された場合、条件関数内で `u[:x]` および `u[:y]` にアクセスできます。
