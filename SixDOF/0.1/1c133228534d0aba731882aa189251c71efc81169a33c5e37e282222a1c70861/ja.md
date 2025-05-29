```
MotorPropBatteryDataFit(CT2, CT1, CT0, CQ2, CQ1, CQ0, D, num, type,
    R, Kv, i0, voltage)
```

**入力**

  * CT2, CT1, CT0: プロペラ推力係数の二次フィットの形式: CT = CT2*J2 + CT1*J + CT0
  * CQ2, CQ1, CQ0: プロペラトルク係数の二次フィットの形式: CQ = CQ2*J2 + CQ1*J + CQ0
  * D: プロペラ直径
  * num: プロペラの数
  * type: CO (トルクが加算される), COUNTER (トルクが加算されるが符号が反転), COCOUNTER (トルクなし、打ち消し合う)
  * R: モーター抵抗
  * Kv: モーターKv
  * i0: モーター無負荷電流
  * voltage: バッテリー電圧

```
