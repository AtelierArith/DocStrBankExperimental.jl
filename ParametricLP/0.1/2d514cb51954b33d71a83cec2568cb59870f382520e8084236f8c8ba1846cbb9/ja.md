```
find_regions(
    model::JuMP.Model,
    parameters::Vector{VariableRef},
    box::Tuple{Tuple{Float64,Float64},Tuple{Float64,Float64}},
    ϵ = 0.01,
)
```

この関数は、線形計画法の `model` において、2つの `parameters` に関するすべての最適基底とそれに対応する領域を見つけます。

### 必要な引数

`model` は、右辺の値のうち2つが変数に置き換えられた形で定義された `JuMP.Model` の線形プログラムです。

`parameters` は、パラメトリックに探索したい2つの制約の右辺に現れる2つの変数のベクトルです。

`box` はタプルのタプルで、上記の `parameters` のそれぞれの最小値と最大値を定義します。

### オプションの引数

`ϵ` は、隣接する基底を見つける際に使用される許容値です。
