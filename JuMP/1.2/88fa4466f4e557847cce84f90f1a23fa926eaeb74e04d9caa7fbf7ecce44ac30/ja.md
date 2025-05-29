```
struct VectorConstraint
```

ベクトル制約のデータ。`func`フィールドには関数を表すJuMPオブジェクトが含まれ、`set`フィールドにはMOIセットが含まれています。`shape`フィールドには、制約が構築された形式に一致する[`AbstractShape`](@ref)が含まれています（例：行列やフラットベクトルを使用して）。JuMPの制約の表現に関する[ドキュメント](@ref Constraints)も参照してください。
