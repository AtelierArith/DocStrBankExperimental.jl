`HYPREAlgorithm(solver; Pl = nothing)`

[HYPRE.jl](https://github.com/fredrikekre/HYPRE.jl) は [`hypre`](https://computing.llnl.gov/projects/hypre-scalable-linear-solvers-multigrid-methods) へのインターフェースであり、スパース線形システムのための反復ソルバーと前処理器を提供します。これは主に大規模なマルチプロセス分散問題（MPIを使用）向けに開発されていますが、Juliaの標準スパース行列を使用した単一プロセスの問題にも使用できます。

ソルバー/前処理器のオプションに対してより詳細な制御が必要な場合は、すでに作成されたソルバーを `HYPREAlgorithm`（および `Pl` キーワード引数）に渡すこともできます。特定のオプションでソルバーを設定する方法については、HYPRE.jlのドキュメントを参照してください。

!!! note
    HYPREソルバーを使用するには、Juliaのバージョンが1.9以上である必要があり、パッケージHYPRE.jlがインストールされている必要があります。


## 位置引数

単一の位置引数 `solver` には以下の選択肢があります：

  * `HYPRE.BiCGSTAB`
  * `HYPRE.BoomerAMG`
  * `HYPRE.FlexGMRES`
  * `HYPRE.GMRES`
  * `HYPRE.Hybrid`
  * `HYPRE.ILU`
  * `HYPRE.ParaSails`（前処理器としてのみ）
  * `HYPRE.PCG`

## キーワード引数

  * `Pl`: 左前処理器の選択。

## 例

例えば、`HYPRE.PCG` をソルバーとして使用し、`HYPRE.BoomerAMG` を前処理器として使用する場合、アルゴリズムは以下のように定義されるべきです：

```julia
A, b = setup_system(...)
prob = LinearProblem(A, b)
alg = HYPREAlgorithm(HYPRE.PCG)
prec = HYPRE.BoomerAMG
sol = solve(prob, alg; Pl = prec)
```
