```
truncate(uv::TheoreticalDistributionScalarValue,
    constraint::TruncateStd, n::Int = 10000)
```

`uv`を使用して理論的分布を`TruncateStd`サンプリング制約で切り詰めます。

この関数は切り詰められた分布の平均と標準偏差を計算する必要があるため、これを可能にするために追加のオプション引数`n_draws`を取ります。
