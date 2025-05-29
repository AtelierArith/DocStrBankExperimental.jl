```
evaluate(
    A::ExaFMM{F},
    x::Vector{F},
    fmmoptions::ModifiedHelmholtzFMMOptions{I, F}
) where {I, F <: Real}
```

新しい値 `x` に対して事前構築された FMM 構造 `A` を評価します。

# 引数

  * `A::ExaFMM{F}`: すべての割り当てられた変数へのポインタを持つ ExaFMM 構造。
  * `x::Vector{F}`: 各ソース位置での電荷などの値。
  * `fmmoptions::ModifiedHelmholtzFMMOptions{I, F}`: セットアップ関数のための Julia 修正ヘルムホルツ初期化子、識別子として使用されます。
