```
SpinSqueezing(ρ::AbstractMatrix; basis="Dicke", output="KU")
```

入力密度行列のスピン圧縮パラメータを計算します。`basis`は、ディッケ基底のための`"Dicke"`またはパウリ基底のための`"Pauli"`を指定できます。`output`は、キタガワとウエダによって定義されたスピン圧縮のための`"KU"`と、ウィンランドらによって定義されたスピン圧縮のための`"WBIMH"`の両方を指定できます。
