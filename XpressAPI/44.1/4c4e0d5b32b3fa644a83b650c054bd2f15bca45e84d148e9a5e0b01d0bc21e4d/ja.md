```
XPRSdelgencons(prob, ncons, conind)::prob
```

一般制約を問題から削除します。

# 引数

  * `prob::XPRSprob`: 現在の問題。
  * `ncons::Integer`: 削除する一般制約の数。
  * `conind::AbstractVector{Integer}`: 削除する一般制約を含む長さ `ncons` の整数配列。

# 戻り値

  * `prob::XPRSprob`: 現在の問題。

C APIの対応する関数のドキュメントも参照してください [XPRSdelgencons](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSdelgencons.html)。
