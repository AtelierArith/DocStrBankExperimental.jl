```
ParameterMessageBehavior()
```

`ParameterMessageBehavior` は、`ParameterReq` および `ParameterRsp` メッセージを介してパラメータをサポートしたいエージェントのタスクを簡素化します。パラメータを提供するエージェントは、`params(a)` メソッド（またはインデックス付きパラメータの場合は `params(a, ndx)` メソッド）を実装することで、そのパラメータを広告できます。このメソッドは、名前とシンボルのペアのリストを返します。各エントリは、指定された名前を持つパラメータを表し、指定されたシンボルを使用してディスパッチされます。パラメータの取得および設定リクエストは、`get(a, Val(symbol))` および `set(a, Val(symbol), value)` メソッド（またはインデックス付きパラメータの場合は `get(a, Val(symbol), ndx)` および `set(a, Val(symbol), ndx, value)`）にディスパッチされます。メソッドが定義されていない場合、同じ名前のエージェント構造体フィールドが存在すれば、それがパラメータのバックとして使用されます。

セッターは、設定された値を返すべきであり、それによって要求元のエージェントに返すことができます。セッターが `nothing` を返す場合、実際の値はゲッターを使用して取得され、その後要求元のエージェントに送信されます。

エージェントは、特定のパラメータを広告しないことを選択することができ、パラメータに対して `isunlisted(Val(symbol))` メソッドを定義して `true` を返すことができます。同様に、エージェントは、パラメータを読み取り専用としてマークすることを選択でき、パラメータに対して `isreadonly(Val(symbol))` メソッドを定義して `true` を返すことができます。

パラメータ変更イベントは、パラメータに対して `onparamchange(a::Agent, b::Behavior, param, ndx, value)` メソッドを定義することでキャプチャできます。

エージェントのデフォルトの `init()` は、自動的に `ParameterMessageBehavior` を追加してエージェントのパラメータをディスパッチ処理し、したがってエージェントは明示的にこれを追加することなくこの動作の恩恵を受けることができます。エージェントが独自の `init()` メソッドを提供し、パラメータをサポートしたい場合は、`init()` 中にこの動作を追加する必要があります。

# 例:

```julia
using Fjage

@agent struct MyAgent
  param1::Int = 1
  param2::Float64 = 0.0
  secret::String = "top secret message"
  x::Int = 2
end

Fjage.param(a::MyAgent) = [
  "MyAgent.param1" => :param1,    # backed by a.param1
  "MyAgent.param2" => :param2,    # backed by a.param2, but readonly
  "MyAgent.X" => :X,              # backed by getter and setter
  "MyAgent.Y" => :Y,              # backed by getter only, so readonly
  "MyAgent.secret" => :secret     # backed by a.secret, but unlisted
]

Fjage.isreadonly(a::MyAgent, ::Val{:param2}) = true
Fjage.isunlisted(a::MyAgent, ::Val{:secret}) = true

Fjage.get(a::MyAgent, ::Val{:X}) = a.x
Fjage.set(a::MyAgent, ::Val{:X}, value) = (a.x = clamp(value, 0, 10))
Fjage.get(a::MyAgent, ::Val{:Y}) = a.x + 27
```
