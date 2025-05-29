```julia
SparseHamiltonian(funcs, mats; unit, dimensionless_time)

```

`SparseHamiltonian`型のコンストラクタ。`funcs`と`mats`は、時間依存関数のリストと対応する行列のリストです。ハミルトニアンは$∑ᵢfuncs[i](s)×mats[i]$として表現できます。`unit`は、`funcs`と`mats`を定義する際に`:h`または`:ħ`のいずれが1に設定されるかを指定します。`unit`が`:h`の場合、`mats`は$2π$でスケーリングされます。
