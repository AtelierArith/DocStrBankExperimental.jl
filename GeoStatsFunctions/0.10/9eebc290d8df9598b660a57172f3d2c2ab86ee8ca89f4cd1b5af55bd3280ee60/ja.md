```
EmpiricalVariogram(partition, var₁, var₂=var₁; [options])
```

地理空間 `partition` の変数 `var₁` と `var₂` の経験的（交差）変動関数を、Hoffimann & Zadrozny 2019 に従って計算します。

`options` を地理空間データを用いた基礎となる [`EmpiricalVariogram`](@ref) 呼び出しに渡します。

## 参考文献

  * Hoffimann, J and Zadrozny, B. 2019. [Efficient variography with partition variograms](https://www.sciencedirect.com/science/article/pii/S0098300419302936)
