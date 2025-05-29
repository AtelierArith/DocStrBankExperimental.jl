```
IntegrationProfiler{opType, optsType, DEAlg, DEOpts}
```

微分方程系の統合を使用して尤度関数をプロファイリングするプロファイラメソッドです。

### フィールド

  * `reoptimize::Bool`: `integrator`の各ステップ後に再最適化するかどうかを示します。デフォルトは`false`です。
  * `optimizer::opType`: 最適化プロセスに使用される最適化器。デフォルトは`nothing`です。
  * `optimizer_opts::optsType`: 最適化器のオプション。デフォルトは`NamedTuple()`です。
  * `integrator::DEAlg`: 統合に使用される微分方程式アルゴリズム。
  * `integrator_opts::DEOpts`: 微分方程式ソルバーのオプション。デフォルトは`NamedTuple()`です。
  * `matrix_type::Symbol`: ヘッセ行列近似に使用される行列のタイプ。可能なオプションは`:hessian`、`:identity`です。デフォルトは`:hessian`です。
  * `gamma::Float64`: フルヘッセ行列が計算されていない場合（例：`matrix_type = :identity`）に統合に使用される補正係数。デフォルトは`1.0`です。

### 例

```julia
using OrdinaryDiffEq
profiler = IntegrationProfiler(integrator = Tsit5(), integrator_opts = (dtmax=0.3,), matrix_type = :hessian)
```
