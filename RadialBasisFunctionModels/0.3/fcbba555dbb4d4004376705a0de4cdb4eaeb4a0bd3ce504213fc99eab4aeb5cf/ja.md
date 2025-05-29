```
RBFMachineWithKernel(; φ, features, labels, poly_deg)
```

内部に `model :: RBFModel`（または `model == nothing`）を保持するコンテナです。内部モデルは、`fit!` を呼び出した後にデータを補間します。特徴の配列の配列は `features` フィールドに格納されます。同様に、`labels` にも格納されます。`add_data!` の後、モデルは再度フィッティングされる必要があり、そのことはフィールド `is_valid` によって示されます。

より一般的な RBFModel と対照的に、単一の RBF 関数（すなわち、1 セットの形状パラメータ）のみを使用する必要があります。
