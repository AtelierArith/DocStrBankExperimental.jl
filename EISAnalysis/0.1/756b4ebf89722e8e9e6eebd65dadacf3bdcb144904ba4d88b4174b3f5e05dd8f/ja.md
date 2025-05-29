```
circuit_fit(circuit, ω_data,Z_data)
```

EISデータに回路をフィッティングするためのメイン関数です。

初期推定値は回路定義を通じて暗黙的に渡されます。例:     randles_circuit = 0.23r-(r-0.025wo^80)/0.2c     # p0 = [0.23,1.0,(0.025,80),0.2]

# 属性

  * `circuit`: フィッティングする回路
  * `ω_data`: EIS周波数
  * `Z_data`: EISインピーダンス
