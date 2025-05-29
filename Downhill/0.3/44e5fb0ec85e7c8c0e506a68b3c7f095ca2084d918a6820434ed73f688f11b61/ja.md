```
optimize!(
    fdf, M::OptBuffer, x₀;
    gtol=1e-6,
    convcond=nothing,
    maxiter=100,
    maxcalls=nothing,
    reset=true,
    constrain_step=nothing,
    tracking=nothing,
    verbosity=0
)
```

`fdf`の最適化を行い、初期近似値`x₀`から始めます。

# 引数

  * `M::OptBuffer`: 最適化に使用するコアメソッド
  * `fdf(x, g)::Function`: 最適化する関数。タプル(f(x), ∇f(x))を返し、`g`が可変の場合は勾配で上書きする必要があります。
  * `x0`: 初期近似値

# キーワード

## 収束基準

収束基準を指定するための2つのオプションがあります。デフォルトは`gtol`によるもので、2つ目はカスタム停止`convcond`によるものです。

  * `gtol::Real`: (デフォルトの停止基準) 勾配の2ノルムが以下のときに最適化を停止します
  * `convcond=(x, xpre, y, ypre, g)->Bool`: 引数の値、関数の値、及び`g`radientに基づくカスタム停止基準の関数。`nothing`の場合（デフォルト）、`gtol`に対応し、指定された場合は`gtol`基準が無視されます。

例（デフォルト基準）: `convcond = (x, xpre, y, ypre, g) -> norm(g, 2) ≤ gtol`。

## 最適化の制限

`maxiter`および/または`maxcalls`を指定することで最適化プロセスを（制限）解除します。

  * `maxiter::Integer`: この回数の反復後に最適化を強制的に停止します（反復回数を制約しないには`nothing`または負の値を使用）
  * `maxcalls::Integer`: この回数の関数呼び出し後に最適化を強制的に停止します（呼び出し回数を制約しないには`nothing`または負の値を使用）

## 最適化制約

最適化の不等式制約は`constrain_step`によって処理されます。

  * `constrain_step(x0, d)`: `x0`から方向`d`へのステップを制約する関数。`x0 + αd`が許可される最大ステップである実数値`α`を返す必要があります。

## 初期化

  * `reset=true`: 最適化プログラムの`init!`メソッドにキーワード引数として渡す値

## 最適化パス

  * `tracking::Union{Nothing,IO,AbstractString}`: 最適化プロセスをログするためのIOストリームまたはファイル名、またはログを無効にするための`nothing`（デフォルト: `nothing`）
  * `verbosity::Integer`: ロギングの冗長性。`0`（デフォルト）はトラッキングを無効にします。`1`は目的関数評価のすべての点を対応する値と勾配と共にログします。`2`は線形探索に関する追加統計を表示します。`tracking == nothing`の場合はオプションが無視されます。
