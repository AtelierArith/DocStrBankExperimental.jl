```
rotMatrix = teme2tod_matrix(JD)
```

与えられたTTユリウス日を使用して、IAU-76モデルに基づくTEMEからTODへの回転行列を見つけます。

入力値は、通常のSOFA方式で2つの部分に分けられたユリウス日であり、時間解像度を保持するように設計されています。完全なユリウス日は、ベクトルの2つの成分を加えることで単一の数値として利用可能です。

TEMEベクトルをTODに変換するために使用されます `r_TOD = rotMatrix * r_TEME`

ValladoのTEMEフレームの説明から派生しています。TEMEは完全には公開されておらず、その定義の曖昧な性質により、いくつかの誤りを含む可能性があることに注意してください。
