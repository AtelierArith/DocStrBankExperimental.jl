```
StabilityDeriv(CL0, CLalpha, CLq, CLM, CLdf, CLde, alphas, 
    CD0, U0, exp_Re, e, Mcc, CDdf, CDde, CDda, CDdr, 
    CYbeta, CYp, CYr, CYda, CYdr, Clbeta, 
    Clp, Clr, Clda, Cldr, 
    Cm0, Cmalpha, Cmq, CmM, Cmdf, Cmde, 
    Cnbeta, Cnp, Cnr, Cnda, Cndr)
```

航空機の安定性導関数。ほとんどは安定性導関数に慣れている場合は自明です（例：CLalphaはdCL/dalphaまたは揚力曲線の傾き）。あまり馴染みのないものには以下が含まれます。

  * M: マッハ数
  * alphas: ストールの迎角
  * U0: 参照レイノルズ数CD0が計算された速度
  * exp_Re: 粘性摩擦係数の分母の係数（0.5は層流、0.2は乱流）
  * e: オズワルド効率係数
  * Mcc: 峰値臨界マッハ数（圧縮性抗力の上昇が始まるとき）
