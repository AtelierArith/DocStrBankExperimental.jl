```
FRD(w, r)
```

周波数応答データを表します。`w`は周波数ベクトルを保持し、`r`は応答を保持します。この型に定義されているメソッドには以下が含まれます。

  * `+,-,*`
  * `length, vec, sqrt`
  * `plot`
  * `feedback`
  * [`freqvec`](@ref)
  * [`tfest`](@ref) を使用して有理モデルを推定
  * 周波数領域でのインデクシング、例えば `G[1Hz : 5Hz]`、`G[1rad : 5rad]`

もし `r` がMIMO周波数応答を表す場合、次元は `ny × nu × nω` です。

オブジェクト `frd::FRD` は、`using Plots` が呼ばれている場合、`plot(frd, hz=false)` を使用してプロットできます。
