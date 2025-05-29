```
flux_godunov(u_ll, u_rr, orientation, equations::InviscidBurgersEquation1D)
```

無粘性バージェス方程式のためのゴドノフ（アップウィンド）数値フラックス。詳細は https://metaphor.ethz.ch/x/2019/hs/401-4671-00L/literature/mishra*hyperbolic*pdes.pdf の4.1.5節、特に式(4.16)を参照してください。
