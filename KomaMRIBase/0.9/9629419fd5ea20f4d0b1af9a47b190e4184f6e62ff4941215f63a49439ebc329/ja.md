```
times = get_adc_sampling_times(seq)
```

シーケンス `seq` のサンプルが取得される時刻の配列を返します。

# 引数

  * `seq`: (`::Sequence`) シーケンス構造体

# 返り値

  * `times`: (`::Vector{Float64}`, `[s]`) サンプルが取得される時刻の配列
