```
apply(filt::SavitzkyGolayFilter, spec::Spectrum, applyLLD=false)
```

`spec`のチャネルデータに関数を適用します（低レベルのディスクリミネーターあり/なし）。関数はカウントデータの関数でなければならず、エネルギースケールやスペクトルの特性を変更することはできません。結果はSpectrumです。

例:

```
apply(SavitzkyGolayFilter{6,4}(),spec)
```
