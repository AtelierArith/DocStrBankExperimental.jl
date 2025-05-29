```
excitation(type, t)
```

異なるタイプの励起信号を計算します

**入力**

  * type : 励起タイプ

    1. `Triangle`
    2. `Rectangle`
    3. `Hammer`
    4. `SmoothRect`
    5. `SineWave`
    6. `HalfSine`
    7. `HaverSine`
    8. `SweptSine`
    9. `GaussianPulse`
    10. `ColoredNoise`
  * `t`: 時間ベクトル

**出力**

  * `F`: 励起信号
