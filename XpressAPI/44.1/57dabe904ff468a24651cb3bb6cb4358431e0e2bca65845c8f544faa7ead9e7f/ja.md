```
XPRSaddsets(prob, nsets, nelems, settype, start, colind, refval)::prob
```

最適化ツールに渡した後に問題にセットを追加することを可能にします。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `nsets::Integer`: 新しいセットの数。
  * `nelems::Integer`: 追加されたセットの新しい非ゼロの数。
  * `settype::AbstractVector{Cchar}`: セットタイプを含む長さ nsets の文字配列: 1 は SOS1 を示し; 2 は SOS2 を示します;
  * `start::AbstractVector{Integer}`: 各セットの要素の開始位置に対する `colind` および `refval` 配列のオフセットを含む長さ `nsets` の整数配列。
  * `colind::AbstractVector{Integer}`: 各セットの要素に対する（連続した）列インデックスを含む長さ `nelems` の整数配列。
  * `refval::AbstractVector{Number}`: （連続した）参照値を含む長さ `nelems` の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C API の対応する関数 [XPRSaddsets](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSaddsets.html) のドキュメントも参照してください。
