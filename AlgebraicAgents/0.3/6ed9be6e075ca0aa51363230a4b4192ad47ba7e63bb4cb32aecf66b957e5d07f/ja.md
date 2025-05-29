```
Opera(uuid2agent_pairs...)
```

動的構造体であり、

  * **エージェントのディレクトリ**（`uuid => agent` ペアの辞書）を含む;
  * **未来（遅延インタラクション）**を追跡し、実行する;
  * **システム制御**を追跡し、実行する;
  * **瞬時のインタラクション**を追跡し、実行する;

# 未来

関数呼び出しをスケジュールし、あらかじめ決められた時点で実行することができます。アクションはタプル `(id, call, time)` としてモデル化され、ここで `id` はアクションのオプションのテキスト識別子であり、`call` は指定された `time` に呼び出される（パラメータなしの）匿名関数です。アクションが実行されると、戻り値と対応するアクション ID および実行時間が `Opera` インスタンスの `futures_log` フィールドに追加されます。

[`add_future!`](@ref) と [`@future`](@ref) を参照してください。

## 例

```julia
alice = MyAgentType("alice")
interact = agent -> wake_up!(agent)
@future alice 5.0 interact(alice) "alice_schedule"
```

ソルバーは `t=5` で停止し、関数 `() -> interact(alice)` を呼び出します（クロージャは `@future` が呼び出された時点で取得されます）。このインタラクションは `"alice_schedule"` として識別されます。

# 制御インタラクション

モデルの各ステップで実行される制御関数呼び出しをスケジュールすることができます。アクションはタプル `(id, call)` としてモデル化され、ここで `id` はアクションのオプションのテキスト識別子であり、`call` は（パラメータなしの）匿名関数です。アクションが実行されると、戻り値と対応するアクション ID および実行時間が `Opera` インスタンスの `controls_log` フィールドに追加されます。

[`add_control!`](@ref) と [`@control`](@ref) を参照してください。

## 例

```julia
system = MyAgentType("system")
control = agent -> agent.temp > 100 && cool!(agent)
@control system control(system) "temperature control"
```

各ステップで、ソルバーは関数 `() -> control(system)` を呼び出します（クロージャは `@future` が呼び出された時点で取得されます）。

# 瞬時のインタラクション

モデルの単一ステップ内で存在する追加のインタラクションをスケジュールすることができます。このようなアクションは、名前付きタプル `(id, priority=0., call)` としてモデル化されます。ここで、`call` は（パラメータなしの）匿名関数です。

これらはモデルの単一ステップ内で存在し、`_prestep!` と `_step!` の呼び出しが終了した後、割り当てられた優先度の順に実行されます。

特に、次の2種類のインタラクションをスケジュールすることができます：

  * `poke(agent, priority)` は、指定された優先度で `() -> _interact!(agent)` という呼び出しに変換されます。
  * `@call opera expresion priority` は、指定された優先度で `() -> expression` という呼び出しに変換されます。

[`poke`](@ref) と [`@call`](@ref) を参照してください。

## 例

```julia
# `poke`
poke(agent, 1.) # `_interact!(agent)` を呼び出す; この呼び出しは優先度1で瞬時の優先度キューに追加されます
```

```julia
# `@call`
bob_agent = only(getagent(agent, r"bob"))
@call agent wake_up(bob_agent) # 優先度0で `() -> wake_up(bob_agent)` に変換されます
```
