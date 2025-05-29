```
evaluate(
    A::ExaFMM{F},
    x::Vector{F},
    fmmoptions::LaplaceFMMOptions{I}
) where {I, F <: Real}
```

事前に構築されたFMM構造体 `A` を新しい値 `x` に対して評価します。

# 引数

  * `A::ExaFMM{F}`: すべての割り当てられた変数へのポインタを持つExaFMM構造体。
  * `x::Vector{F}`: 各ソース位置での電荷などの値。
  * `fmmoptions::LaplaceFMMOptions{I}`: セットアップ関数のためのJulia Laplace初期化子、識別子として使用されます。
