```
set_config(key::AbstractString, val::Bool)
```

設定値をブール値として設定します。

# 引数

  * `key::AbstractString`: 設定するキー。以下の表に可能な `key` の値、そのデフォルト設定、およびその使用法を示します。
  * `val::Bool`: キーに設定する値

| キー                                                    | デフォルト | 説明                                                                       |
|:----------------------------------------------------- |:-----:|:------------------------------------------------------------------------ |
| NORMALIZE*GAS*CONSTANTS                               | true  | 真の場合、混合物に対してモルガス定数 (R) がCODATA値に設定されます                                   |
| CRITICAL*WITHIN*1UK                                   | true  | 真の場合、臨界温度から1 uK以内の任意の温度は臨界点にあると見なされます                                    |
| CRITICAL*SPLINES*ENABLED                              | true  | 真の場合、臨界点の近傍で臨界スプラインが使用されます                                               |
| SAVE*RAW*TABLES                                       | false | 真の場合、生の未圧縮テーブルもファイルに書き込まれます                                              |
| REFPROP*DONT*ESTIMATE*INTERACTION*PARAMETERS          | false | 真の場合、REFPROPのバイナリ相互作用パラメータが推定されると、静かに続行するのではなくエラーをスローします                 |
| REFPROP*IGNORE*ERROR*ESTIMATED*INTERACTION_PARAMETERS | false | 真の場合、REFPROPのバイナリ相互作用パラメータが推定できない場合、失敗するのではなく静かに続行します                    |
| REFPROP*USE*GERG                                      | false | 真の場合、高精度の純流体状態方程式を使用するのではなく、GERG-2008の純流体EOSを使用します                       |
| REFPROP*USE*PENGROBINSON                              | false | 真の場合、高精度の純流体状態方程式を使用するのではなく、ペング・ロビンソンEOSを使用します                           |
| DONT*CHECK*PROPERTY_LIMITS                            | false | 真の場合、可能な場合、CoolPropは値がプロパティ制限内にあるかどうかのチェックをスキップします                       |
| HENRYS*LAW*TO*GENERATE*VLE_GUESSES                    | false | 真の場合、水ベースの混合物の露点計算を行う際に、ヘンリーの法則を使用して液相組成の推測を生成します                        |
| OVERWRITE_FLUIDS                                      | false | 真の場合、すでに存在する流体ライブラリに流体が追加されると、流体を追加せず（おそらく例外をスローするのではなく）、上書きします          |
| OVERWRITE*DEPARTURE*FUNCTION                          | false | 真の場合、追加される出発関数がすでに存在する場合、出発関数を追加せず（おそらく例外をスローするのではなく）、上書きします             |
| OVERWRITE*BINARY*INTERACTION                          | false | 真の場合、追加されるバイナリ相互作用ペアがすでに存在する場合、バイナリ相互作用ペアを追加せず（おそらく例外をスローするのではなく）、上書きします |
