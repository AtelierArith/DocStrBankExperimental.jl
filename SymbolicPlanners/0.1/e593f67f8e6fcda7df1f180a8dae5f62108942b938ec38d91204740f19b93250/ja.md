```
(sim::Simulator)(domain::Domain, state::State, actions, spec)
```

PDDL `domain` で初期 `state` から `actions` の実行をシミュレートします。目標仕様 `spec` はシミュレーションの終了条件として機能し、コストや報酬情報を指定することもできます。
