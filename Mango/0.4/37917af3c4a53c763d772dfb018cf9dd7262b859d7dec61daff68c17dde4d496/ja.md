```
on_step(agent::Agent, world::World, clock::Clock, step_size_s::Real)
```

フックインであり、すべての `agent` のシミュレーションコンテナの各ステップで呼び出されます。

さらに、`world` が渡され、これはエージェントが相互に作用できる環境に対する共通のビューを表します。加えて、`clock` と `step_size_s` は、現在のシミュレーション時間と現在のステップで経過する時間を読み取るために使用できます。
