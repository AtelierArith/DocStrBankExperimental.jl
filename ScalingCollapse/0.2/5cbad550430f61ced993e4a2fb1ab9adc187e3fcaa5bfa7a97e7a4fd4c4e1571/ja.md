```
ScalingProblem(args...; kwargs...)
```

初期化時に解決するスケーリング問題を作成します。

# 引数

  * `xs`: データのx値
  * `ys`: データのy値
  * `es`: データのy誤差値（オプション）
  * `Ls`: データのシステムサイズ

引数の詳細については、methods(ScalingCollapse.unzip_data)を参照してください。

# キーワード引数

  * `sf::ScalingFunction=ScalingFunction(preset; kwargs...)`: スケーリング関数
  * `p_space::Vector{StepRangeLen}=[0.1:0.1:3.0 for _ in sf.p_names]`: パラメータ探索空間
  * `dx::Vector{Float64}=[-Inf, Inf]`: 最適化区間
  * `quality::QualityFunction=Linear()`: 品質関数
  * `quality_scan::QualityFunction=MultipleSplines(scan_mode=true)`: パラメータ空間スキャン用の品質関数（ここではデフォルト関数を使用することを強く推奨します）
  * `verbose::Bool=false`: 最適化中に情報を印刷
  * `starting_ps::Vector{Float64}`: `starting_ps`が指定されている場合、初期パラメータ空間スキャンは行われません。代わりに、最適化は指定された点から開始されます。これははるかに速いですが、グローバルミニマムを見つけられない可能性があります。
  * `error::Bool=true`: `error=true`の場合、誤差分析が実行され、最適パラメータの不確実性の推定が行われます。

# フィールド

  * `data::Vector{Data}`: スケーリングされるデータ
  * `sf::ScalingFunction`: スケーリング関数
  * `p_space::Vector{StepRangeLen}`: 探索パラメータ空間
  * `dx::Vector{Float64}`: 最適化区間
  * `optimal_ps::Vector{Float64}`: 最適パラメータ
  * `optimal_ps_error::Vector{Float64}`: 最適パラメータの不確実性
  * `minimum::Float64`: 目的関数の最小値
  * `solved::Bool`: 最適化が呼び出された場合は`true`
  * `verbose::Bool`: 最適化中に情報を印刷
  * `error::Bool`: 誤差分析を実行
  * `quality_scan::QualityFunction`: パラメータ空間スキャン用の品質関数
  * `quality::QualityFunction`: 品質関数
  * `skip_scan::Bool`: ユーザーによって`starting_ps`が指定されている場合は`true`
  * `starting_ps::Vector{Float64}`: 最適化のための開始点
  * `errors_defined::Bool`: ユーザーによって誤差が指定されている場合は`true`

# 例

```julia
using ScalingCollapse
```

### x軸のみを再スケーリング

```julia
# (例: ys == イジングモデルのバインダ累積量)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:x; p_names=["T_c", "nu"]),
    p_space=[0.1:0.1:3.0, 0.1:0.1:3.0],
    dx=[-1.0, 1.0],
)

# または、同じだが誤差あり
ScalingProblem(xs, ys, es, Ls;
    sc=ScalingFunction(:x; p_names=["T_c", "nu"]),
    p_space=[0.1:0.1:3.0, 0.1:0.1:3.0],
    dx=[-1.0, 1.0],
)
```

### x軸とy軸を再スケーリング

```julia
# (例: ys == イジングモデルの磁化)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xy; p_names=["T_c", "nu", "beta"]),
    dx=[-1.0, 1.0],
)
```

### x軸とy軸を再スケーリング、ただしy軸は負の指数で

```julia
# (例: ys == イジングモデルの感受性)
ScalingProblem(xs, ys, Ls;
    sc=ScalingFunction(:xny; p_names=["T_c", "nu", "gamma"]),
    dx=[-1.0, 1.0],
)
```
