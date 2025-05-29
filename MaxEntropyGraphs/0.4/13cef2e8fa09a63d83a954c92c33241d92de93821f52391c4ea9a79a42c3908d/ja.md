```
project(m::BiCM;   α::Float64=0.05, layer::Symbol=:bottom, precomputed::Bool=true, 
                    distribution::Symbol=:Poisson, adjustment::PValueAdjustment=BenjaminiHochberg(),
                        multithreaded::Bool=false)
```

V-motifと有意水準`α`を組み合わせたp値調整方法`adjustment`を使用して、BiCMモデル`m`の層`layer`への統計的に検証された投影グラフを取得します。

# 引数

  * `α`: 有意水準。
  * `layer`: `layer=:bottom`または`layer=:top`を渡すことで層を指定できます。
  * `precomputed`: trueの場合、二重隣接行列の期待値が使用され、それ以外の場合はモデルパラメータからパラメータが計算されます。
  * `distribution`: p値を計算するために使用される分布。これは`:Poisson`または`:PoissonBinomial`です。
  * `adjustment`: 多重検定のためにp値を調整するために使用される方法。これは`PValueAdjustment`型の任意の方法（`MultipleTesting.jl`を参照）です。デフォルトでは、ベンジャミニ・ホッホバーグ法が使用されます。
  * `multithreaded`: trueの場合、p値はマルチスレッドを使用して計算されます。

# 例

```jldoctest project_bicm
julia> model = BiCM(corporateclub());

julia> solve_model!(model);

julia> project(model, layer=:bottom)
{25, 0} undirected simple Int64 graph

```

```jldoctest project_bicm
julia> project(model, layer=:top)
{15, 0} undirected simple Int64 graph

```
