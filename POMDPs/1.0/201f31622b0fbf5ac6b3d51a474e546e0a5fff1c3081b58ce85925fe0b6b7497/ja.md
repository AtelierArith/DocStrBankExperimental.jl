```
simulate(sim::Simulator, m::POMDP, p::Policy, u::Updater=updater(p), b0=initialstate(m), s0=rand(b0))
simulate(sim::Simulator, m::MDP, p::Policy, s0=rand(initialstate(m)))
```

指定されたポリシーを使用してシミュレーションを実行します。

戻り値の型は柔軟で、シミュレーターに依存します。シミュレーションは[シミュレーション標準](http://juliapomdp.github.io/POMDPs.jl/latest/simulation.html#Simulation-Standard-1)に従う必要があります。
