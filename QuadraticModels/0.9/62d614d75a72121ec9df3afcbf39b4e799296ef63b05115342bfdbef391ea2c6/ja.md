```
qp = QuadraticModel(c, Hrows, Hcols, Hvals; Arows = Arows, Acols = Acols, Avals = Avals, 
                    lcon = lcon, ucon = ucon, lvar = lvar, uvar = uvar, sortcols = false)

qp = QuadraticModel(c, H; A = A, lcon = lcon, ucon = ucon, lvar = lvar, uvar = uvar)
```

オプションの境界 `lvar ≦ x ≦ uvar` とオプションの線形制約 `lcon ≦ Ax ≦ ucon` を持つ二次モデル $min ~\tfrac{1}{2} x^T H x + c^T x + c_0$ を作成します。ユーザーは `QuadraticModel` コンストラクタに `H` の下三角のみを提供する必要があります。

最初のコンストラクタでは、`sortcols = true` の場合、`Hcols` と `Acols` は昇順にソートされます（その後、`Hrows`、`Hvals` と `Arows`、`Avals` もそれに応じてソートされます）。

[`QPSReader.jl`](https://github.com/JuliaSmoothOptimizers/QPSReader.jl) を使用して、QPSファイルから二次モデルを作成することもできます：

```
using QPSReader
qps = readqps("QAFIRO.SIF")
qp = QuadraticModel(qps)
```

作成された `QuadraticModel{T, S, D}` のインスタンスには次のフィールドが含まれています：

  * [`NLPModels.NLPModelMeta`](https://juliasmoothoptimizers.github.io/NLPModels.jl/stable/models/#NLPModels.NLPModelMeta) の型 `meta`  （[`NLPModels.jl`](https://github.com/JuliaSmoothOptimizers/NLPModels.jl) から）、
  * `A` と `H` 行列の入力タイプに依存する型 `QuadraticModels.QPData` の `data`、
  * [`NLPModels.Counters`](https://juliasmoothoptimizers.github.io/NLPModels.jl/stable/reference/#NLPModels.Counters) の型 `counters` （[`NLPModels.jl`](https://github.com/JuliaSmoothOptimizers/NLPModels.jl) から）。

[`NLPModelsModifiers.SlackModel`](https://juliasmoothoptimizers.github.io/NLPModelsModifiers.jl/stable/reference/#NLPModelsModifiers.SlackModel) を使用して、密な行列を持つ `QPData` に基づく `QuadraticModel` を使用すると、フィールド `data` が `SparseMatricesCOO` を持つ `QPData` に変換されます。

二次モデルに特化したそのインプレースバリアント `SlackModel!` は、`SparseMatricesCOO` を持つ `QPData` に基づく `QuadraticModel` のみで機能します。
