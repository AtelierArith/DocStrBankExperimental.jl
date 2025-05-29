```
get_input_pair_index(pair::AbstractString)
```

入力ペア "PT*INPUTS", "HmolarQ*INPUTS" などのインデックスを取得します。これは `abstractstate_update()` 関数で使用されます。

# 引数

  * `pair::AbstractString`: 次の表で説明されている入力ペアの名前

| 入力ペア                | 説明                             |
|:------------------- |:------------------------------ |
| QT_INPUTS           | モル品質、温度（K）                     |
| QSmolar_INPUTS      | モル品質、エントロピー（J/mol/K）           |
| QSmass_INPUTS       | モル品質、エントロピー（J/kg/K）            |
| HmolarQ_INPUTS      | エンタルピー（J/mol）、モル品質             |
| HmassQ_INPUTS       | エンタルピー（J/kg）、モル品質              |
| DmassQ_INPUTS       | モル密度（kg/m^3）、モル品質              |
| DmolarQ_INPUTS      | モル密度（mol/m^3）、モル品質             |
| PQ_INPUTS           | 圧力（Pa）、モル品質                    |
| PT_INPUTS           | 圧力（Pa）、温度（K）                   |
| DmassT_INPUTS       | 質量密度（kg/m^3）、温度（K）             |
| DmolarT_INPUTS      | モル密度（mol/m^3）、温度（K）            |
| HmassT_INPUTS       | エンタルピー（J/kg）、温度（K）             |
| HmolarT_INPUTS      | エンタルピー（J/mol）、温度（K）            |
| SmassT_INPUTS       | エントロピー（J/kg/K）、温度（K）           |
| SmolarT_INPUTS      | エントロピー（J/mol/K）、温度（K）          |
| TUmass_INPUTS       | 温度（K）、内部エネルギー（J/kg）            |
| TUmolar_INPUTS      | 温度（K）、内部エネルギー（J/mol）           |
| DmassP_INPUTS       | 質量密度（kg/m^3）、圧力（Pa）            |
| DmolarP_INPUTS      | モル密度（mol/m^3）、圧力（Pa）           |
| HmassP_INPUTS       | エンタルピー（J/kg）、圧力（Pa）            |
| HmolarP_INPUTS      | エンタルピー（J/mol）、圧力（Pa）           |
| PSmass_INPUTS       | 圧力（Pa）、エントロピー（J/kg/K）          |
| PSmolar_INPUTS      | 圧力（Pa）、エントロピー（J/mol/K）         |
| PUmass_INPUTS       | 圧力（Pa）、内部エネルギー（J/kg）           |
| PUmolar_INPUTS      | 圧力（Pa）、内部エネルギー（J/mol）          |
| DmassHmass_INPUTS   | 質量密度（kg/m^3）、エンタルピー（J/kg）      |
| DmolarHmolar_INPUTS | モル密度（mol/m^3）、エンタルピー（J/mol）    |
| DmassSmass_INPUTS   | 質量密度（kg/m^3）、エントロピー（J/kg/K）    |
| DmolarSmolar_INPUTS | モル密度（mol/m^3）、エントロピー（J/mol/K）  |
| DmassUmass_INPUTS   | 質量密度（kg/m^3）、内部エネルギー（J/kg）     |
| DmolarUmolar_INPUTS | モル密度（mol/m^3）、内部エネルギー（J/mol）   |
| HmassSmass_INPUTS   | エンタルピー（J/kg）、エントロピー（J/kg/K）    |
| HmolarSmolar_INPUTS | エンタルピー（J/mol）、エントロピー（J/mol/K）  |
| SmassUmass_INPUTS   | エントロピー（J/kg/K）、内部エネルギー（J/kg）   |
| SmolarUmolar_INPUTS | エントロピー（J/mol/K）、内部エネルギー（J/mol） |

# 例

```julia
julia> get_input_pair_index("PT_INPUTS")
9
```
