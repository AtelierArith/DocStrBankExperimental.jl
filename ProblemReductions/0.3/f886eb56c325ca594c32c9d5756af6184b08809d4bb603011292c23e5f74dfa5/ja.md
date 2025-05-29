```
AbstractProblem
```

計算問題の抽象ベースタイプ。

### 必要なインターフェース

  * [`num_variables`](@ref)、計算問題の変数の数。
  * [`num_flavors`](@ref)、自由度のフレーバー（ドメイン）の数。
  * [`solution_size`](@ref)、入力構成のサイズ（小さいほど良い）。
  * [`problem_size`](@ref)、計算問題のサイズ。例えば、グラフの場合は `(n_vertices=?, n_edges=?)` となる。
  * [`energy_mode`](@ref)、エネルギー関数の定義。`LargerSizeIsBetter` または `SmallerSizeIsBetter` である。

### 派生インターフェース

  * [`variables`](@ref)、計算問題の自由度。
  * [`flavors`](@ref)、自由度のフレーバー（ドメイン）。
  * [`findbest`](@ref)、入力問題の最良の構成を見つける。
