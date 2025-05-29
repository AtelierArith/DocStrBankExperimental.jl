```
SemOptimizerOptim{A, B} <: SemOptimizer{:Optim}
```

`Optim.jl`に接続し、最適化バックエンドとして機能します。

# コンストラクタ

```
SemOptimizerOptim(;
    algorithm = LBFGS(),
    options = Optim.Options(;f_reltol = 1e-10, x_abstol = 1.5e-8),
    kwargs...)
```

# 引数

  * `algorithm`: `Optim.jl`からの最適化アルゴリズム
  * `options::Optim.Options`: 最適化アルゴリズムのオプション

# 使用法

Optim.jlライブラリのすべてのアルゴリズムとオプションが利用可能です。詳細については、Optim.jlのオンラインドキュメントを参照してください。

# 例

```julia
my_optimizer = SemOptimizerOptim()

# ヘッセ行列に基づく最適化、バックトラッキングラインサーチと修正された初期ステップサイズを使用
using Optim, LineSearches

my_newton_optimizer = SemOptimizerOptim(
    algorithm = Newton(
        ;linesearch = BackTracking(order=3),
        alphaguess = InitialHagerZhang()
    )
)
```

# 拡張ヘルプ

## 制約付き最適化

`Fminbox`または`SAMIN`制約付き最適化アルゴリズムを使用する場合、各モデルパラメータの下限および上限のベクトルまたは辞書を`lower_bounds`および`upper_bounds`キーワード引数を介して指定できます。あるいは、`lower_bound`および`upper_bound`キーワード引数を使用して、すべての非分散モデルパラメータのデフォルトの境界を指定し、`variance_lower_bound`および`variance_upper_bound`キーワードを分散パラメータ（*S*行列の対角線）に対して指定できます。

## インターフェース

  * `algorithm(::SemOptimizerOptim)`
  * `options(::SemOptimizerOptim)`

## 実装

`SemOptimizer`のサブタイプです。
