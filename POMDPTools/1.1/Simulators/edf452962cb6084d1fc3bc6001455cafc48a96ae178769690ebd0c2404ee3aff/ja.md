```
Sim(m::POMDP, p::Policy, metadata=(note="ノート",))
Sim(m::POMDP, p::Policy[, updater[, initial_belief[, initialstate]]]; kwargs...)
```

`Sim`オブジェクトを作成して、POMDPシミュレーションを表します。
