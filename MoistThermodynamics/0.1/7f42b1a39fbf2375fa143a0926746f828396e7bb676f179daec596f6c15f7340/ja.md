```
air_density(T, p[, q::PhasePartition])
```

状態方程式（理想気体の法則）からの（湿った）空気の密度は次の通りです。

  * `T` 空気温度
  * `p` 圧力

そして、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気のものになります。
