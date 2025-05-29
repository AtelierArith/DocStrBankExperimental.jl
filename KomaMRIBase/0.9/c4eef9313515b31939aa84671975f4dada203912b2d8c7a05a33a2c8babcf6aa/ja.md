```
A = ampls(g::Grad)
A = ampls(r::RF)
A = ampls(d::ADC)
```

MRIシーケンスイベントの振幅サンプルを取得します。

# 引数

  * `gr`: (`::Grad`) グラデients構造体
  * `rf`: (`::RF`) RF構造体
  * `adc`: (`::ADC`) ADC構造体

# 戻り値

  * `A`: (`::Vector{Number}`) 振幅サンプルを含むベクトル
