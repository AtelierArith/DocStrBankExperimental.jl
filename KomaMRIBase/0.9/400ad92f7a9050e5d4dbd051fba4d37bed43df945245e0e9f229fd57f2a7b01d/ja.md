```
samples = get_samples(seq::Sequence; off_val=0, max_rf_samples=Inf)
```

`seq`のイベントのサンプルを返します。

# 引数

  * `seq`: (`::Sequence`) Sequence構造体

# キーワード

  * `off_val`: (`::Number`, `=0`) 振幅のオフセット値。通常、`Inf`に設定することでプロット内のポイントを隠すために使用されます。
  * `max_rf_samples`: (`::Integer`, `=Inf`) RF構造体の最大サンプル数

# 返り値

  * `samples`: (`::NamedTuple`) `gx`、`gy`、`gz`、`rf`、および`adc`イベントのサンプルを含みます。各イベントは`e::NamedTuple`で表され、時間サンプル（`e.t`）と振幅サンプル（`e.A`）を含みます。
