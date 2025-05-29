```
totransfermap(nq::Integer, circuit::Vector{Gate}, thetas=nothing)
```

`nq`量子ビットに作用するパウリ転送マップを、パラメータ`thetas`を持つ回路から計算します。`thetas`はデフォルトで`nothing`ですが、回路にパラメータ化されたゲートが含まれている場合は必要です。返されるルックアップマップは、[(pstr1, coeff1), (pstr2, coeff2), ...]のようなベクトルのベクトルであり、ここで`pstr`は影響を受ける量子ビット上の*部分的*パウリ文字列です。
