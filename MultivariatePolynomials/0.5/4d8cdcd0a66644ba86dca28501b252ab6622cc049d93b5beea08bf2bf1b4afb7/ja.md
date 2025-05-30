```
struct GeneralizedEuclideanAlgorithm <: AbstractUnivariateGCDAlgorithm
    primitive_rem::Bool
    skip_last::Bool
end
```

多項式の最大公約数を計算するアルゴリズムで、ユニーク因子分解環上の係数を持つ多項式に対して一般化されたユークリッドアルゴリズムを使用します。詳細は[Knu14, Algorithm E, p. 426-427]を参照してください。

`primitive_rem`が`true`の場合、多項式除算で生成される中間剰余は原始的になります。`primitive_part`が`false`に設定されている場合、結果の剰余のみが原始的になります（一般化されたユークリッドアルゴリズムの中間剰余は依然として原始的にする必要があります）。

[Knu14] Knuth, D.E., 2014. *Art of computer programming, volume 2: Seminumerical algorithms.* Addison-Wesley Professional. 第3版。
