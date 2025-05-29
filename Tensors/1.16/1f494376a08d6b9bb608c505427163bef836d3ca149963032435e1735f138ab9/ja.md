```
eigen(A::SymmetricTensor{4})
```

対称4次テンソルの固有値と2次固有テンソルを計算し、`FourthOrderEigen`オブジェクトを返します。固有値と固有テンソルは、固有値の昇順にソートされます。

関連情報として、[`eigvals`](@ref) と [`eigvecs`](@ref) を参照してください。
