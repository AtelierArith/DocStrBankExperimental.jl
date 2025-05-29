```
initial_guess(m::DBCM, method::Symbol=:degrees)
```

DBCMモデル`m`の最大尤度パラメータの初期推定値を`method`を使用して計算します。

利用可能な方法は次のとおりです：

  * `:degrees`（デフォルト）：初期推定値はグラフの次数を使用して計算されます。すなわち、$\theta = [-\log(d_{out}); -\log(d_{in})]$
  * `:degrees_minor`：初期推定値はグラフの次数とエッジの数を使用して計算されます。すなわち、$\theta = [-\log(d_{out}/(\sqrt{E} + 1)); -\log(d_{in}/(\sqrt{E} + 1) )]$
  * `:random`：初期推定値は0と1の間のランダムな値を使用して計算されます。すなわち、$\theta_{i} = -\log(r_{i})$ ここで、$r_{i} \sim U(0,1)$
  * `:uniform`：初期推定値は均等に0.5に設定されます。すなわち、$\theta_{i} = -\log(0.5)$
  * `:chung_lu`：初期推定値はグラフの次数とエッジの数を使用して計算されます。すなわち、$\theta = [-\log(d_{out}/(2E)); -\log(d_{in}/(2E))]$

# 例

```jldoctest
julia> model = DBCM(MaxEntropyGraphs.Graphs.SimpleDiGraph(rhesus_macaques()));

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:degrees_minor);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model);

```
