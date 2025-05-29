```
impedance(impedance_system,ω, U0 ,
          excited_spec, excited_bc, excited_bcval,
           dmeas_stdy,
           dmeas_tran 
           )
    
```

インピーダンスを計算します。

  * ω: 周波数
  * U0: 定常状態の解
  * dmeas_stdy: 測定関数の定常状態部分の導関数
  * dmeas_tran: 測定関数の過渡部分の導関数
