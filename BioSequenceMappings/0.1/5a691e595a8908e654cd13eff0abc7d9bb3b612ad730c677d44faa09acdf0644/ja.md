```
site_specific_frequencies(X::AbstractAlignment[, weights=X.weights]; as_vec=false)
```

`X`のサイト特異的周波数を返します。`as_vec`が真の場合、結果は長さ`Lxq`のベクトルです。そうでない場合、結果は`q`行`L`列の行列（デフォルト）です。
