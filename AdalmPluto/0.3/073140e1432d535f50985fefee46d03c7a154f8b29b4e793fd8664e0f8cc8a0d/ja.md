```
recv(pluto, nbSamples)
```

JuliaバッファからnbSamplesを読み取ります。JuliaバッファにnbSamples未満のサンプルがある場合、残りのサンプルが読み取られ、バッファが再充填され、合計でnbSamplesが読み取られます。新しく割り当てられた`Array{ComplexF32}`を返します。

# 引数

  * `pluto::PlutoSDR` : サンプルを受信するためのラジオ。
  * `nbSamples::Int` : 受信するサンプルの数。

# 戻り値

  * `buffer::Array{ComplexF32}` : nbSamplesの複素値を持つ配列。
