```
NonlinearSolvePolyAlgorithm(algs; start_index::Int = 1)
```

`NonlinearProblem` と `NonlinearLeastSquaresProblem` のための PolyAlgorithms を定義する一般的な方法です。これは、成功するまで順番に試されるアルゴリズムのタプルのコンテナです。どれも成功しなかった場合は、残差が最も低いアルゴリズムが返されます。

### 引数

  * `algs`: 順番に試すアルゴリズムのタプル！(これがタプルでない場合、返されるアルゴリズムは型安定ではありません)。

### キーワード引数

  * `start_index`: 開始するインデックス。デフォルトは `1` です。

### 例

```julia
using NonlinearSolve

alg = NonlinearSolvePolyAlgorithm((NewtonRaphson(), Broyden()))
```
