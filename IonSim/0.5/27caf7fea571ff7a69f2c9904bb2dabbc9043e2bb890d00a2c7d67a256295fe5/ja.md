```
displace(v::VibrationalMode, α::Number; method="truncated")
```

`v`に対応する変位演算子$D(α)$を返します。

`method="truncated"`（デフォルト）の場合、行列要素は$D(α) = exp[αa^† - α^*a]$に従って計算され、ここで$a$と$a^†$は次元`modecutoff(v)+1`の切断されたヒルベルト空間に存在します。それ以外の場合、`method="analytic"`の場合、行列要素は無限次元のヒルベルト空間を仮定して計算されます。一般に、このオプションはユニタリ演算子を返しません。
