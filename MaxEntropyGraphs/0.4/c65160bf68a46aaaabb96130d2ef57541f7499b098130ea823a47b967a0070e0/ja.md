```
initial_guess(m::BiCM; method::Symbol=:degrees)
```

BiCMモデル`m`の最大尤度パラメータの初期推定値を`method`を使用して計算します。

利用可能な方法は次のとおりです：

  * `:degrees`（デフォルト）：初期推定値はグラフの次数を使用して計算されます。すなわち、$\theta = [-\log(d_{ot}); -\log(d_{	op})]$
  * `:random`：初期推定値は0と1の間のランダムな値を使用して計算されます。すなわち、$\theta_{i} = -\log(r_{i})$ ただし、$r_{i} \sim U(0,1)$
  * `:uniform`：初期推定値は一様に0.5に設定されます。すなわち、$\theta_{i} = -\log(0.5)$
  * `:chung_lu`：初期推定値はグラフの次数とエッジの数を使用して計算されます。すなわち、$\theta = [-\log(d_{ot}/(2E)); -\log(d_{	op}/(2E))]$

# 例

```jldoctest
julia> model = BiCM(corporateclub());

julia> initial_guess(model, method=:random);

julia> initial_guess(model, method=:uniform);

julia> initial_guess(model, method=:chung_lu);

julia> initial_guess(model);

```
