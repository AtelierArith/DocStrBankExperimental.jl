```
t = times(gr::Grad)
t = times(rf::RF)
t = times(adc::ADC)
```

MRIシーケンスイベントの時間サンプルを取得します。

# 引数

  * `gr`: (`::Grad`) グラデーション構造体
  * `rf`: (`::RF`) RF構造体
  * `adc`: (`::ADC`) ADC構造体

# 戻り値

  * `t`: (`::Vector{Number}`) 時間サンプルを含むベクター
