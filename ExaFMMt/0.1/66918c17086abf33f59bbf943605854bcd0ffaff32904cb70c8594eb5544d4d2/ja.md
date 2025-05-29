```
evaluate(
    A::ExaFMM{C},
    x::Vector{C},
    fmmoptions::HelmholtzFMMOptions{I, C}
) where {I, C <: Complex}
```

新しい値 `x` に対して事前構築された FMM 構造 `A` を評価します。

# 引数

  * `A::ExaFMM{C}`: すべての割り当てられた変数へのポインタを持つ ExaFMM 構造。
  * `x::Vector{C}`: 各ソース位置での電荷などの値。
  * `fmmoptions::HelmholtzFMMOptions{I, C}`: セットアップ関数のための Julia Helmoltz 初期化子、識別子として使用されます。
