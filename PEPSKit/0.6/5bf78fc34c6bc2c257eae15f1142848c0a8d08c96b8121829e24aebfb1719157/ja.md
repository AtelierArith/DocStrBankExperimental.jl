```
fixedpoint(operator, peps₀::InfinitePEPS, env₀::CTMRGEnv; kwargs...) -> peps_final, env_final, cost_final, info
# expert version:
fixedpoint(operator, peps₀::InfinitePEPS, env₀::CTMRGEnv, alg::PEPSOptimize; finalize!=OptimKit._finalize!)
```

`operator`の不動点（すなわち基底状態）を、提供された最適化パラメータに従って`peps₀`から開始して見つけます。初期環境`env₀`は、最初のCTMRG実行のための初期推測として機能します。デフォルトでは、ランダムな初期環境が使用されます。

最適化パラメータは、キーワード引数を介して、または直接`PEPSOptimize`構造体として提供できます。サポートされているキーワード引数は以下の通りです。

## キーワード引数

### 一般設定

  * `tol::Real=0.0001` : 最適化者の勾配ノルム収束の全体的な許容誤差。関連する許容誤差（境界および境界勾配の許容誤差など）を、明示的に指定されない限り、妥当なデフォルトに設定します。
  * `verbosity::Int=1` : 全体的な出力情報の冗長性レベルで、以下のいずれかである必要があります：

    0. すべての出力を抑制
    1. 警告のみを表示
    2. 初期化および収束情報
    3. 反復情報
    4. AD出力を含むデバッグ情報
  * `reuse_env::Bool=true` : `true`の場合、現在の最適化ステップは前の環境で初期化されます。そうでない場合は、ランダムな環境が使用されます。
  * `symmetrization::Union{Nothing,SymmetrizationStyle}=nothing` : `nothing`または`SymmetrizationStyle`を受け入れ、その場合、PEPSおよびPEPS勾配は各最適化反復後に対称化されます。
  * `(finalize!)=OptimKit._finalize!` : 各最適化ステップの後に`finalize!`関数呼び出しを挿入します。これは、`OptimKit.optimize`の`finalize!`キーワード引数を利用します。この関数は`(peps, env), f, g = finalize!((peps, env), f, g, numiter)`をマッピングします。

### 境界アルゴリズム

境界アルゴリズムのパラメータは、`boundary_alg::Union{NamedTuple,<:CTMRGAlgorithm}`を介して、キーワード引数の`NamedTuple`または`CTMRGAlgorithm`を直接使用して提供します。すべての可能なキーワード引数の説明については、[`leading_boundary`](@ref)を参照してください。デフォルトでは、`tol=1e-4tol`のCTMRG許容誤差が使用されます。

### 勾配アルゴリズム

勾配アルゴリズムのパラメータは、`gradient_alg::Union{NamedTuple,Nothing,<:GradMode}`を介して、キーワード引数の`NamedTuple`、`nothing`、または`GradMode`構造体を直接使用して提供します。`nothing`を渡すと、CTMRG実行を完全に微分し、すべての反復が考慮されることを意味します。サポートされている`NamedTuple`キーワード引数は以下の通りです：

  * `tol::Real=1e-2tol` : 不動点勾配反復の収束許容誤差。
  * `maxiter::Int=30` : 勾配問題の最大反復回数。
  * `alg::Symbol=:linsolver` : 勾配アルゴリズムのバリアントで、以下のいずれかである必要があります：

      * `:geomsum` : 幾何級数から直接勾配を計算します。詳細は[`GeomSum`](@ref)を参照してください。
      * `:manualiter` : 勾配幾何級数を手動で反復します。詳細は[`ManualIter`](@ref)を参照してください。
      * `:linsolver` : 反復ソルバーを使用して不動点勾配線形問題を解決します。詳細は[`LinSolver`](@ref)を参照してください。
      * `:eigsolver` : シルベスター方程式の固有値定式を介して勾配を決定します。詳細は[`EigSolver`](@ref)を参照してください。
  * `verbosity::Int` : 勾配出力の冗長性で、デフォルトでは≤0で過度の印刷を無効にします。デバッグ目的でのみ>0にする必要があります。
  * `iterscheme::Symbol=:fixed` : 微分のモードを決定するCTMRG反復スキーム。これは以下のいずれかです：

      * `:fixed` : 微分されたCTMRG反復は、固定されたゲージのセットを使用して事前に計算されたSVDを使用します。
      * `:diffgauge` : 微分された反復はCTMRG反復とその後のゲージ固定ステップで構成され、ゲージ固定手順も微分されます。

### 最適化者設定

最適化アルゴリズムは、`optimizer_alg::Union{NamedTuple,<:OptimKit.OptimizationAlgorithm}`を介して、キーワード引数の`NamedTuple`または`OptimKit.OptimizationAlgorithm`を直接使用して提供します。デフォルトでは、`OptimKit.LBFGS`が`HagerZhangLineSearch`と組み合わせて使用されます。サポートされているキーワード引数は以下の通りです：

  * `alg::Symbol=:lbfgs` : 最適化アルゴリズムで、以下のいずれかである必要があります：

      * `:gradientdescent` : 勾配降下アルゴリズム。詳細は[OptimKit README](https://github.com/Jutho/OptimKit.jl)を参照してください。
      * `:conjugategradient` : 共役勾配アルゴリズム。詳細は[OptimKit README](https://github.com/Jutho/OptimKit.jl)を参照してください。
      * `:lbfgs` : L-BFGSアルゴリズム。詳細は[OptimKit README](https://github.com/Jutho/OptimKit.jl)を参照してください。
  * `tol::Real=tol` : 最適化者の勾配ノルム許容誤差。
  * `maxiter::Int=100` : 最大最適化ステップ数。
  * `verbosity::Int=3` : 最適化者出力の冗長性。
  * `lbfgs_memory::Int=20` : BFGSヘッセ行列の制限付きメモリ表現のサイズ。

## 戻り値

この関数は、最終的なPEPS、CTMRG環境、コスト値、および以下のエントリを含む情報`NamedTuple`を返します：

  * `last_gradient` : コスト関数の最後の勾配。
  * `fg_evaluations` : コストおよび勾配関数の評価回数。
  * `costs` : コスト値の履歴。
  * `gradnorms` : 勾配ノルムの履歴。
  * `truncation_errors` : 境界アルゴリズムの最大切断誤差の履歴。
  * `condition_numbers` : CTMRG環境の最大条件数の履歴。
  * `gradnorms_unitcell` : 各ユニットセルエントリの勾配ノルムの履歴。
  * `times` : 最適化ステップの実行時間の履歴。

```
