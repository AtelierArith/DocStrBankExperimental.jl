```
MotorPropBatteryDataFit(CT2, CT1, CT0, CQ2, CQ1, CQ0, D, num, type,
    R, Kv, i0, voltage)
```

**Inputs**

  * CT2, CT1, CT0: quadratic fit to propeller thrust coefficient of form: CT = CT2*J2 + CT1*J + CT0
  * CQ2, CQ1, CQ0: quadratic fit to propeller torque coefficient of form: CQ = CQ2*J2 + CQ1*J + CQ0
  * D: propeller diameter
  * num: number of propellers
  * type: CO (torques add), COUNTER (torques add but with minus sign), COCOUNTER (no torque, they cancel out)
  * R: motor resistance
  * Kv: motor Kv
  * i0: motor no-load current
  * voltage: battery voltage
