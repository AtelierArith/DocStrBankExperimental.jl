```
XPRScopyprob(dest, src, name)::dest
```

1つの問題に定義された情報を別の問題にコピーします。

# 引数

  * `dest::XPRSprob`: 情報がコピーされる新しい問題ポインタ。
  * `src::XPRSprob`: 情報がコピーされる古い問題ポインタ。
  * `name::Union{Nothing,AbstractString}`: 問題のコピーの名前を含む、`nothing` 終端を含む最大1024文字の文字列。

# 戻り値

  * `dest::XPRSprob`: 情報がコピーされる新しい問題ポインタ。

C APIの対応する関数のドキュメント [XPRScopyprob](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRScopyprob.html) も参照してください。
