```
AcousticSource(pos, frequency; spl=0)
AcousticSource(x, z, frequency; spl=0)
AcousticSource(x, y, z, frequency; spl=0)
```

位置 `pos` にある音源で、名目上の `frequency` と音源レベル `spl` (dB re 1 µPa @ 1 m)。音源は全方向性であり、点音源としてよく近似されると仮定されています。音源にはいくつかの帯域幅があるかもしれませんが、名目上の周波数は、吸収、反射係数などの伝播効果を推定するために使用されます。

音源の位置が不明な場合は、`nothing` として指定できます。これは、伝播モデルが音源の位置を必要としない場合（例：データ駆動モデル）に便利です。
