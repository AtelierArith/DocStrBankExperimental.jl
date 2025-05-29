```
initial_guess(m::UBCM, method::Symbol=:degrees)
```

UBCMモデル`m`の最大尤度パラメータの初期推定値を`method`を使用して計算します。

利用可能な方法は次のとおりです：

  * `:degrees`（デフォルト）：初期推定値はグラフの次数を使用して計算されます。すなわち、$\theta_{i} = -\log(d_{i})$
  * `:degrees_minor`：初期推定値はグラフの次数とエッジの数を使用して計算されます。すなわち、$\theta_{i} = -\log(d_{i}/(\sqrt{E} + 1))$
  * `:random`：初期推定値は0と1の間のランダムな値を使用して計算されます。すなわち、$\theta_{i} = -\log(r_{i})$ ここで、$r_{i} \sim U(0,1)$
  * `:uniform`：初期推定値は均等に0.5に設定されます。すなわち、$\theta_{i} = -\log(0.5)$
  * `:chung_lu`：初期推定値はグラフの次数とエッジの数を使用して計算されます。すなわち、$\theta_{i} = -\log(d_{i}/(2E))$

# 例

```jldoctest
julia> model = UBCM(MaxEntropyGraphs.Graphs.SimpleGraphs.smallgraph(:karate));

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:degrees_minor);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model)
11-element Vector{Float64}:
 -0.0
 -0.6931471805599453
 -1.0986122886681098
 -1.3862943611198906
 -1.6094379124341003
 -1.791759469228055
 -2.1972245773362196
 -2.302585092994046
 -2.4849066497880004
 -2.772588722239781
 -2.833213344056216

```
