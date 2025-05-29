```
XPRSchgobjn(prob, objidx, ncols, colind, objcoef)::prob
```

マルチオブジェクティブ問題における目的関数の1つまたは複数の係数を修正します。

目的がすでに存在する場合、`colind`および`objcoef`配列に存在しない係数は変更されません。目的が存在しない場合は、問題に追加されます。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `objidx::Integer`: 追加または修正する目的関数のインデックス。
  * `ncols::Integer`: 変更する目的関数係数要素の数。
  * `colind::AbstractVector{Integer}`: 目的係数が変更される列のインデックスを含む長さ`ncols`の整数配列。
  * `objcoef::AbstractVector{Number}`: 新しい目的関数係数を与える長さ`ncols`の倍精度配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数[XPRSchgobjn](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSchgobjn.html)のドキュメントも参照してください。
