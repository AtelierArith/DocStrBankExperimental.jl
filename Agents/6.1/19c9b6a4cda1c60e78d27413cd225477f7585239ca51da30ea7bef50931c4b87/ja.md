```
StandardABM <: AgentBasedModel
```

[`AgentBasedModel`](@ref) の具体的な実装であり、エージェントベースのモデリング研究で最も一般的に使用されます。これは離散時間で動作します。入力として、少なくとも1つ、または最大2つの関数が必要です：エージェントステッピング関数とモデルステッピング関数です。シミュレーションの各離散ステップで、エージェントステッピング関数がすべてのスケジュールされたエージェントに対して1回適用され、モデルステッピング関数がモデルに対して1回適用されます。

連続時間のバリアントについては、[`EventQueueABM`](@ref) を参照してください。

`StandardABM` を構築するには、次の構文を使用します：

```
StandardABM(AgentType(s) [, space]; properties, agent_step!, model_step!, kwargs...)
```

モデルは、指定された `space` に住む `AgentType(s)` 型のエージェントを期待します。`AgentType(s)` は [`@agent`](@ref) または `@multiagent` またはエージェント型の `Union` の結果です。

`space` は `AbstractSpace` のサブタイプであり、利用可能なすべてのスペースについては [Space](@ref Space) を参照してください。省略すると、すべてのエージェントは仮想的に1つの位置にあり、空間構造はありません。スペースは可変オブジェクトであり、モデル間で共有するようには設計されていません。これを行う必要がある場合は、同じプロパティを持つスペースの新しいインスタンスを作成してください。

進化ルールは、キーワード `agent_step!`、`model_step!` に与えられた関数です。

## キーワード

  * `agent_step!`: スケジュールされた各 `agent` に対して呼び出される、`agent_step!(agent, model)` の形式でなければならないオプションのエージェントステッピング関数です。
  * `model_step!`: `model_step!(model)` の形式でなければならないオプションのモデルステッピング関数です。`agent_step!` または `model_step!` のいずれかは必ず指定する必要があります。複雑なモデルの場合、モデルを進化させるために `model_step!` のみを使用する方が適している場合があります。以下の「高度なステッピング」例を参照してください。
  * `container = Dict`: エージェントが格納されるコンテナの型です。シミュレーション中にエージェントが削除されない場合は `Vector` を使用します。これにより、エージェントをより効率的に格納でき、エージェントの取得と反復が速くなります。シミュレーション中にエージェントが削除されることが予想される場合は `Dict` を使用します。
  * `properties = nothing`: ユーザーがモデルに含めることができる追加のモデルレベルのプロパティです。`properties` は任意のデータのコンテナであり得ますが、最も一般的には `Symbol` キーを持つ `Dict` または合成型（`struct`）です。
  * `scheduler = Schedulers.fastest`: エージェントの（デフォルトの）アクティベーション順序を決定するスケジューラです。詳細なオプションについては [scheduler API](@ref Schedulers) を参照してください。デフォルトでは、すべてのエージェントが可能な限り最速の順序で1ステップごとに1回アクティブ化されます。`agent_step!` 関数が指定されていない場合、`scheduler` は完全に無視されます。この場合、ユーザーがスケジューリングを制御すると仮定されます。例えば、以下の「高度なステッピング」例のように。
  * `rng = Random.default_rng()`: モデルがすべてのランダム関数呼び出しで使用する乱数生成器です。`AbstractRNG` の任意のサブタイプを受け入れます。
  * `agents_first::Bool = true`: エージェントを最初にスケジュールしてアクティブ化し、その後 `model_step!` 関数を呼び出すか、その逆かを指定します。`agent_step!` が指定されていない場合は無視されます。
  * `warn=true`: `AgentType(s)` に対していくつかの型テストが行われ、適切な場合にはデフォルトで警告が表示されます。

## 高度なステッピング

一部の高度なモデルでは、スケジューリングの特別な処理が必要な場合や、エージェントを複数回スケジュールし、単一のシミュレーションステップ中に異なる関数で異なるエージェントのサブセットに作用する必要がある場合があります。そのようなシナリオでは、すべてのダイナミクスが含まれるモデルステッピング関数のみを提供する方が理にかなっています。

自動化された `agent_step!` オプションを使用しない場合、進化中に削除されたエージェントを手動で確認する必要があることに注意してください。これは [`hasid`](@ref) 関数を使用して行います。

以下はその例です：

```julia
function complex_model_step!(model)
    # tip: これらのスケジューラはモデルのプロパティとして定義されるべきです
    scheduler1 = Schedulers.Randomly()
    scheduler2 = user_defined_function_with_model_as_input
    for id in scheduler1(model)
        agent_step1!(model[id], model)
    end
    intermediate_model_action!(model)
    for id in scheduler2(model)
        # ここで `agent_step2!` はエージェントを削除する可能性があるため、手動で確認します
        hasid(model, id) || continue
        agent_step2!(model[id], model)
    end
    if model.step_counter % 100 == 0
        model_action_every_100_steps!(model)
    end
    final_model_action!(model)
    return
end
```
