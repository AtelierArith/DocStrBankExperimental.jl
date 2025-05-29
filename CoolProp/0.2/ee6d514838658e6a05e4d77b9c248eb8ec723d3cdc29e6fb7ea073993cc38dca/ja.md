```
HAPropsSI(output::AbstractString, name1::AbstractString, value1::Real, name2::AbstractString, value2::Real, name3::AbstractString, value3::Real)
```

HAPropsSI関数のDLLラッパー。

# 引数

  * `output`: 望ましいプロパティの出力名、受け入れられる値は以下の表に示されています
  * `name1`, `name2`, `name3`: 与えられた状態値の入力名、1つは「P」でなければなりません

# 注意

ここでは、すべての出力はこれら3つの関数として計算されます: 「Y」（水のモル分率）、 「T」と「P」、 「P」は必須であるため、「Y」と「T」が与えられると（または少なくともそのうちの1つが）より高いパフォーマンスが得られます。

| パラメータ名               | 説明                  | 単位        | 公式                                   |
|:-------------------- |:------------------- |:--------- |:------------------------------------ |
| Omega HumRat W       | 湿度比                 |           |                                      |
| psi_w Y              | 水のモル分率              | mol_w/mol |                                      |
| Tdp T_dp DewPoint D  | 湿度点温度               | K         |                                      |
| Twb T_wb WetBulb B   | 湿球温度                | K         |                                      |
| Enthalpy H Hda       | エンタルピー              | J/kg_da   |                                      |
| Hha                  | 湿った空気1kgあたりのエンタルピー  | J/kg_ha   |                                      |
| InternalEnergy U Uda | 内部エネルギー             | J/kg_da   |                                      |
| Uha                  | 湿った空気1kgあたりの内部エネルギー | J/kg_ha   |                                      |
| Entropy S Sda        | エントロピー              | J/kg_da/K |                                      |
| Sha                  | 湿った空気1kgあたりのエントロピー  | J/kg_ha/K |                                      |
| RH RelHum R          | 相対湿度                |           |                                      |
| Tdb T_db T           | 温度                  | K         |                                      |
| P                    | 圧力                  | Pa        |                                      |
| V Vda                | 比容積                 | m^3/kg_da | $MolarVolume*(1+HumidityRatio)/M_ha$ |
| Vha                  | 湿った空気1kgあたりの比容積     | m^3/kg_ha | $MolarVolume/M_ha$                   |
| mu Visc M            | 粘度                  |           |                                      |
| k Conductivity K     | 導電率                 |           |                                      |
| C cp                 | 定圧比熱容量              | J/kg_da/K |                                      |
| Cha cp_ha            | 湿った空気1kgあたりの定圧比熱容量  | J/kg_ha/K |                                      |
| CV                   | 定容比熱容量              | J/kg_da/K |                                      |
| CVha cv_ha           | 湿った空気1kgあたりの定容比熱容量  | J/kg_ha/K |                                      |
| P_w                  | 水の部分圧               |           |                                      |
| isentropic_exponent  | 等エントロピー指数           |           |                                      |
| speed*of*sound       | 音速                  |           | $sqrt(1/M_ha*cp/cv*dpdrho__constT)$  |
| Z                    | 圧縮率                 |           | $P*MolarVolume/(R*T)$                |

# 例

```julia
# 温度、圧力、および相対湿度に対するエンタルピー（kg乾燥空気あたりJ）
julia> h = HAPropsSI("H", "T", 298.15, "P", 101325, "R", 0.5)
50423.45039247604
# 前のエンタルピーでの飽和空気の温度
julia> T = HAPropsSI("T", "P", 101325, "H", h, "R", 1.0)
290.9620891952412
# 飽和空気の温度 - 入力の順序は重要ではない
julia> T = HAPropsSI("T", "H", h, "R", 1.0, "P", 101325)
290.9620891952412
```

# 参照

HumidAir::HAPropsSI(const char* OutputName, const char* Input1Name, double Input1, const char* Input2Name, double Input2, const char* Input3Name, double Input3);
