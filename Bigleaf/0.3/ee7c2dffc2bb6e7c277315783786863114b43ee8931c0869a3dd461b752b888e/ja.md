```
extraterrestrial_radiation(doy::Number; ...)
extraterrestrial_radiation(datetime::TimeType; ...)
```

地球外の太陽放射を偏心率補正付きで計算します。計算はLanini, 2010（ベルン大学の修士論文）に従います。

# 引数

  * doy: 1から始まる年の日数（DoY）を表す整数

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 

      * solar_constant
  * `year`=2030: タイムスタンプを作成する年。歳差のため、結果は数十年ごとにわずかに変化します。
  * `FT=typeof(constants.solar_constant)`: 戻り値の浮動小数点型を指定

# 値

タイプ`FT`の地球外放射（W_m-2）。

# 例

```jldoctest; output = false
ex_rad = extraterrestrial_radiation(1)
≈(ex_rad, 1414, atol = 1)
# output
true
```
