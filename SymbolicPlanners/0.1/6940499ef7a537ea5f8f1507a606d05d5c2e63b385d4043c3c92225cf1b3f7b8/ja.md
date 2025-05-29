```
(sim::Simulator)(sol::Solution, domain::Domain, state::State, [spec])
```

`sol`の実行を初期`state`から始まるPDDL`domain`内でシミュレートします。目標仕様`spec`を提供することで、シミュレーションの終了条件として使用したり、コストや報酬情報を指定したりすることができます。
