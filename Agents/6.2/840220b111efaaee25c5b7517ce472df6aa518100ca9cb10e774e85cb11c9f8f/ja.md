```
AgentEvent(; action!, propensity, kinds, timing)
```

[`EventQueueABM`](@ref) に渡すことができるイベントインスタンスです。

  * `action! = dummystep`: イベントが対応するエージェントに作用する関数 `action!(agent, model)` です。このキーワードは必須です。`action!` 関数は、Agents.jl による自動生成のイベントに関係なく、新しいイベントを生成するために [`add_event!`](@ref) を呼び出すことができます。
  * `propensity = 1.0`: 定数の実数であるか、イベントの傾向を返す関数 `propensity(agent, model)` であることができます。この関数は、指定された `agent` に対して新しいイベントが生成されるときに呼び出されます。
  * `types = AbstractAgent`: `action!` 関数が適用できるエージェントのタイプです。
  * `timing = Agents.exp_propensity`: イベントが生成された後、どれくらいの時間でトリガーされるかを決定します。デフォルトでは、エージェントに適用可能なすべてのイベントの総傾向をパラメータとする指数分布からランダムにサンプリングされた時間です。すなわち、デフォルトでは「ギレスピー」アルゴリズムがイベントのタイミングに使用されます。あるいは、カスタム関数 `timing(agent, model, propensity)` を指定することもでき、これが時間を返します。

[`add_event!`](@ref) 関数を使用する際には、`event_idx` と `t` が指定されている場合、`propensity` と `timing` は無視されることに注意してください。
