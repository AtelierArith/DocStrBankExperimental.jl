```
BigleafConstants(;...)
```

Bigleaf.jlパッケージ全体で使用される定数

デフォルト値はコンストラクタの名前付き引数によって上書きできます：

  * cp           : 定圧の空気の比熱 (J K-1 kg-1)
  * Rgas         : 普遍気体定数 (J mol-1 K-1)
  * Rv           : 水蒸気の気体定数 (J kg-1 K-1) (Stull 1988 p.641)
  * Rd           : 乾燥空気の気体定数 (J kg-1 K-1) (Foken p. 245)
  * Md           : 乾燥空気のモル質量 (kg mol-1)
  * Mw           : 水蒸気のモル質量 (kg mol-1)
  * eps          : 水蒸気と乾燥空気の分子量の比 (=Mw/Md)
  * g            : 重力加速度 (m s-2)
  * solar_constant: 太陽定数 (W m-2)
  * pressure0    : 海面での基準大気圧 (Pa)
  * Tair0        : 基準空気温度 (K)
  * k            : ボルン・カーマン定数
  * Cmol         : 炭素のモル質量 (kg mol-1)
  * Omol         : 酸素のモル質量 (kg mol-1)
  * H2Omol       : 水のモル質量 (kg mol-1)
  * sigma        : ステファン・ボルツマン定数 (W m-2 K-4)
  * Pr           : プラントル数
  * Sc_CO2       : CO2のシュミット数
  * Kelvin       : 摂氏からケルビンへの変換
  * DwDc         : 水蒸気とCO2の分子拡散率の比
  * days2seconds : 1日あたりの秒数
  * kPa2Pa       : キロパスカル (kPa) からパスカル (Pa) への変換
  * Pa2kPa       : パスカル (Pa) からキロパスカル (kPa) への変換
  * umol2mol     : マイクロモル (umol) からモル (mol) への変換
  * mol2umol     : モル (mol) からマイクロモル (umol) への変換
  * kg2g         : キログラム (kg) からグラム (g) への変換
  * g2kg         : グラム (g) からキログラム (kg) への変換
  * kJ2J         : キロジュール (kJ) からジュール (J) への変換
  * J2kJ         : ジュール (J) からキロジュール (kJ) への変換
  * se*median    : 平均の標準誤差 (SE) を中央値のSEに変換 (http://influentialpoints.com/Training/standard*error*of*median.htm)
  * frac2percent : 分数とパーセントの間の変換

## 例

```jldoctest; output=false
BigleafConstants().g == 9.81
# 月では重力定数を地球の1/6に変更
BigleafConstants(g = BigleafConstants().g/6).g == 9.81/6
# 出力
true
```
