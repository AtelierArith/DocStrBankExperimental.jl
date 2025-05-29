```julia
mutable struct StateMachine{T}
```

汎用状態遷移機能型。

例

```julia
bar!(usrdata) = IncrementalInference.exitStateMachine
foo!(usrdata) = bar!

sm = StateMachine(next=foo!)
usrdata = nothing
while st(usrdata); end
```

ノート

  * また、IncrementalInference/test/testStateMachine.jlも参照してください。
