```
add_agent!([pos,] model::ABM, args...) → newagent
add_agent!([pos,] model::ABM; kwargs...) → newagent
```

これらの2つのバージョンのいずれかを使用して、モデルのエージェントタイプのコンストラクタを使用して新しいエージェントを作成し、追加します。オプションで、エージェントを追加する位置を*最初の引数*として提供できます。これは空間位置タイプと一致する必要があります。

この関数は、エージェントのID*と*位置を設定することを処理します。追加で提供された`args...`または`kwargs...`は、エージェントコンストラクタの他のフィールドに伝播されます（以下の例を参照）。`args...`と`kwargs...`を混在させることはできず、フィールドを設定するために使用できるのは2つのうちの1つだけです。

```
add_agent!([pos,] A::Type, model::ABM, args...) → newagent
add_agent!([pos,] A::Type, model::ABM; kwargs...) → newagent
```

混合エージェントモデルの場合は、これらの2つのバージョンのいずれかを使用します。`A`は作成したいエージェントタイプであり、そうでなければ`A`のコンストラクタを推測することはできません。

## 例

```julia
using Agents
@agent struct Agent(GraphAgent)
    w::Float64 = 0.1
    k::Bool = false
end
model = StandardABM(Agent, GraphSpace(complete_digraph(5)))

add_agent!(model, 1, 0.5, true) # 不正: id/posは内部で設定されます
add_agent!(model, 0.5, true) # 正: wは0.5になります
add_agent!(5, model, 0.5, true) # 位置5に追加、wは0.5になります
add_agent!(model; w = 0.5) # キーワードを使用: wは0.5になり、kはfalseのままです
```
