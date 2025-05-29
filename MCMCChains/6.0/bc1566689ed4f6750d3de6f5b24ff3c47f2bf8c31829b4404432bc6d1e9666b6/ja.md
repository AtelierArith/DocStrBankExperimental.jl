```
cor(chains[; sections, append_chains = true, kwargs...])
```

チェーンのピアソン相関行列を計算します。

`append_chains=false`を設定すると、各チェーンの相関行列を含むデータフレームのベクトルが返されます。
