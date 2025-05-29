```
PEtabODEProblem(model::PEtabModel; kwargs...)
```

`model` からパラメータ推定/推論のための `PEtabODEProblem` を作成します。

オプション（`kwargs`）が提供されていない場合、`ODESolver`、勾配法、およびヘッセ行列法のデフォルト設定が使用されます。デフォルトオプションの詳細については、ドキュメントを参照してください。

また、[`ODESolver`](@ref)、[`SteadyStateSolver`](@ref)、および [`PEtabModel`](@ref) も参照してください。

# キーワード引数

  * `odesolver::ODESolver`: 尤度（目的関数）を計算するためのODEソルバーオプション。
  * `odesolver_gradient::ODESolver`: 勾配を計算するためのODEソルバーオプション。提供されていない場合は `odesolver` がデフォルトとなります。
  * `ss_solver::SteadyStateSolver`: 尤度を計算するための定常状態ソルバーオプション。定常状態シミュレーションを持つモデルにのみ適用されます。
  * `ss_solver_gradient::SteadyStateSolver`: 勾配を計算するための定常状態ソルバーオプション。提供されていない場合は `ss_solver` がデフォルトとなります。
  * `gradient_method::Symbol`: 勾配を計算するための方法。利用可能なオプションとデフォルトはドキュメントに記載されています。
  * `hessian_method::Symbol`: ヘッセ行列を計算するための方法。勾配と同様に、利用可能なオプションとデフォルトはドキュメントに記載されています。
  * `FIM_method=nothing`: 統計的フィッシャー情報行列（FIM）を計算するための方法。`hessian_method` と同じオプションを受け入れます。
  * `sparse_jacobian=false`: ODEモデルを解く際にスパースヤコビアンを使用するかどうか。これにより、大規模モデルのパフォーマンスが大幅に向上する可能性があります。
  * `sensealg`: 勾配計算のための感度アルゴリズム。利用可能なオプションとデフォルトは `gradient_method` に依存します。詳細はドキュメントを参照してください。
  * `chunksize=nothing`: 勾配とヘッセ行列のために前方モード自動微分を使用する際の ForwardDiff.jl のチャンクサイズ。提供されていない場合はデフォルト値が使用されます。`chunksize` を調整することでパフォーマンスが向上する可能性がありますが、簡単ではありません。
  * `split_over_conditions::Bool=false`: 勾配および/またはヘッセ行列を計算する際に、シミュレーション条件にまたがって ForwardDiff.jl の呼び出しを分割するかどうか。条件特有のパラメータが多いモデルではパフォーマンスが向上しますが、そうでない場合は実行時間が増加します。
  * `reuse_sensitivities::Bool=false`: ガウス-ニュートンヘッセ行列近似のために勾配計算から前方感度を再利用するかどうか。`hessian_method=:GaussNewton` および `gradient_method=:ForwardEquations` の場合にのみ適用されます。最適化アルゴリズムが勾配とヘッセ行列の両方を同時に計算する場合、これによりパフォーマンスが大幅に向上する可能性があります。
  * `verbose::Bool = false`: `PEtabODEProblem` を構築する際に進行状況を表示するかどうか。

## 戻り値

`PEtabODEProblem` で、主要なフィールドは次のとおりです：

  * `nllh`: 入力ベクトル `x` に対する負の対数尤度関数を計算します； `nllh(x)`。この関数および以下にリストされている関数の入力 `x` は、`Vector` または `ComponentArray` のいずれかであることができます。
  * `grad!`: nllh のインプレース勾配を計算します； `grad!(g, x)`。
  * `grad`: nllh のアウトオブプレース勾配を計算します； `g = grad(x)`。
  * `hess!`: nllh のインプレースヘッセ行列を計算します； `hess!(H, x)`。
  * `hess`: nllh のアウトオブプレースヘッセ行列を計算します； `H = hess(x)`。
  * `FIM`: nllh のアウトオブプレース統計的フィッシャー情報行列（FIM）を計算します； `F = FIM(x)`。
  * `chi2`: nllh のカイ二乗検定統計量を計算します（以下の数学的定義を参照）； `χ² = chi2(x)`。
  * `residuals`: 測定データとモデル出力の間の残差を計算します（以下の数学的定義を参照）； `r = residuals(x)`。
  * `simulated_values`: 測定テーブル内の各測定に対する対応するモデル値を、測定が現れるのと同じ順序で計算します。
  * `lower_bounds`: パラメータ推定のための下限パラメータ境界。`model` を作成する際に指定されたもの。
  * `upper_bounds`: パラメータ推定のための上限パラメータ境界。`model` を作成する際に指定されたもの。

## 説明

[PEtab標準](https://petab.readthedocs.io/en/latest/) に従い、`PEtabODEProblem` によって作成されるパラメータ推定に使用される目的関数は尤度関数であり、事前分布が提供されている場合は事後関数です。目的の特性は `PEtabModel` で定義されています。実際には、数値的安定性のために、`PEtabODEProblem` は負の対数尤度で動作します：

$$
-\ell(\mathbf{x}) =  - \sum_{i = 1}^N \ell_i(\mathbf{x}),
$$

ここで、$\ell_i$ は各測定 $i$ の尤度です。さらに、数値最適化パッケージに対応するために、`PEtabODEProblem` は指定されたまたはデフォルトの `gradient_method` および `hessian_method` を使用して、勾配 $-\nabla \ell(\mathbf{x})$ および二次導関数ヘッセ行列 $-\nabla^2 \ell(\mathbf{x})$ を計算するための効率的な関数を提供します。

$$
-\ell
$$

およびその導関数に加えて、`PEtabODEProblem` は診断およびモデル選択のための関数を提供します。χ²（カイ二乗）値はモデル選択に使用でき、各測定のχ²値の合計として計算されます。測定 `y`、可観測量 `h = obs_formula`、および標準偏差 `σ = noise_formula` に対して、χ²は次のように計算されます：

$$
\chi^2 = \frac{(y - h)^2}{\sigma^2}
$$

残差 $r$ は測定誤差モデルを評価するために使用でき、次のように計算されます：

$$
r = \frac{(y - h)}{\sigma}
$$

最後に、統計的フィッシャー情報行列（FIM）は同定可能性分析に使用できます。理想的には、正確なヘッセ行列法で計算されるべきです。FIMの逆行列は共分散行列の下限を提供します。FIMは有用ですが、プロファイル尤度アプローチは一般的に同定可能性分析においてより良い結果をもたらします。

1. Cedersund et al, The FEBS journal, pp 903-922 (2009).
2. Raue et al, Bioinformatics, pp 1923-1929 (2009).

```
