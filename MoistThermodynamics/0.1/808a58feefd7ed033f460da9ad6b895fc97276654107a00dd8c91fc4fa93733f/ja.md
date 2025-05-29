```
air_pressure(T, ρ[, q::PhasePartition])
```

状態方程式（理想気体の法則）からの空気圧であり、

  * `T` 空気温度
  * `ρ` （湿）空気密度

および、オプションで、

  * `q` [`PhasePartition`](@ref)。この引数がない場合、結果は乾燥空気に対するものです。
