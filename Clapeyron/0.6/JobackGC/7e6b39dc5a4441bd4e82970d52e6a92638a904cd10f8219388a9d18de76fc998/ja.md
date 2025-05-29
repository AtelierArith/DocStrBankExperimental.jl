```
JobackGC
```

ジョバック法を用いたグループ寄与計算を含むモジュールです。利用可能な関数は次のとおりです：

  * `JobackGC.T_c(model::JobackModel)`: 臨界温度（K単位）
  * `JobackGC.P_c(model::JobackModel)`: 臨界圧力（Pa単位）
  * `JobackGC.V_c(model::JobackModel)`: 臨界体積（m3/mol単位）
  * `JobackGC.T_b(model::JobackModel)`: 常沸点（K単位）
  * `JobackGC.H_form(model::JobackModel)`: 298Kにおける生成エンタルピー、理想気体（J/mol単位）
  * `JobackGC.G_form(model::JobackModel)`: 298Kにおける生成ギブズエネルギー、理想気体（J/mol単位）
  * `JobackGC.S_form(model::JobackModel)`: 298Kにおける生成エントロピー、理想気体（J/mol/K単位）
  * `JobackGC.H_fusion(model::JobackModel)`: 融解エンタルピー（1 atmにおけるJ/mol単位）
  * `JobackGC.H_vap(model::JobackModel)`: 蒸発のモルエンタルピー（常沸点におけるJ/mol単位）
  * `JobackGC.C_p(model::JobackModel, T)`: 理想気体の等圧比熱（J/mol/K単位）
  * `JobackGC.Visc(model::JobackModel, T)`: 液体の動的粘度（Pa*s単位）
