```
random_offdiagonal(offdiagonals::AbstractOffdiagonals)
random_offdiagonal(ham::AbstractHamiltonian, address)
-> newaddress, probability, matrixelement
```

単一のランダム励起を生成します。つまり、`ham`によって表されるハミルトニアン行列の`address`に対応する列のアクセス可能なオフダイアゴナル要素の1つを選択します。あるいは、アクセス可能な行列要素に対するイテレータを引数として渡すこともできます。

[`AbstractHamiltonian`](@ref) インターフェースの一部です。
