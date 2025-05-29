```
bulkformulae(atemp,aqh,speed,sst,hu=10,ht=2,hq=2,zref=10,atmrho=1.2)
```

単位: atemp  - 高さ ht (m) での平均気温 (K)  aqh    - 高さ hq (m) での平均湿度 (kg/kg) speed  - 高さ hu (m) での平均風速 (m/s)     sst    - 海面温度 (K)

バルク公式の定式化:

```
風応力 = (ust,vst) = rhoA * Cd * Ws * (del.u,del.v)
顕熱フラックス = fsha = rhoA * Ch * Ws * del.T * CpAir
潜熱フラックス = flha = rhoA * Ce * Ws * del.Q * Lvap
                 = -Evap * Lvap
```

ここで Cd,Ch,Ce = 抵抗係数、スタントン数、ダルトン数 [無次元] であり、高さと安定性の関数であり、

```
Ws = 風速 = sqrt(del.u^2 +del.v^2)
del.T = Tair - Tsurf
del.Q = Qair - Qsurf
```
