```
virtual_temp(Tair,pressure,VPD; ...)
```

仮想温度は、乾燥空気が実際の温度での湿った空気と同じ密度を持つ温度として定義されます。

# 引数

  * `Tair`:      空気温度 (℃)
  * `pressure`:  大気圧 (kPa)
  * `VPD`:       水蒸気圧不足 (kPa)
  * `Esat_formula`: [`Esat_from_Tair`](@ref) で使用される式

オプション 

  * `constants=`[`BigleafConstants`](@ref)`()`: エントリを持つ辞書 

      * :Kelvin - 摂氏からケルビンへの変換
      * :eps - 水蒸気と乾燥空気の分子量の比 (-)

# 詳細

仮想温度は次のように与えられます：

`Tv = Tair / (1 - (1 - eps) e/pressure)`

ここで、Tairはケルビン（内部で変換されます）です。同様に、VPDは内部で[`VPD_to_e`](@ref)を使用して実際の水蒸気圧（kPaでのe）に変換されます。

# 値

仮想温度 (℃)

# 参考文献

  * Monteith J.L., Unsworth M.H., 2008: Principles of Environmental Physics.           第3版. Academic Press, ロンドン.

# 例

```jldoctest; output = false
Tair,pressure,VPD = 25.0,100.0,1.5
vt = virtual_temp(Tair,pressure,VPD)  
≈(vt, 26.9, atol =0.1)
# output
true
```
