```
mapspectra(f, echogram[; freqdim, distributed])
```

関数 `f` を `DimArray` `echogram` の各スペクトルに適用します。デフォルトでは音響周波数が次元 `:F` に記録されていると仮定しますが、そうでない場合は `freqdim` 引数を使用して次元の名前を指定してください。
