```
agent_hierarchy_mmd(a; use_uuid = 0)
```

この関数は、具体的なモデルのエージェント階層を表示するのに役立ちます。ユーザーが具体的なモデルのインスタンス化を視覚化するために結果をMermaidダイアグラムに渡したいと仮定しています。キーワード引数 `use_uuid` は、各エージェントの名前の後にアンダースコアを付けて、最後の `use_uuid` 桁を追加します。これは、名前だけではユニークなエージェントを区別することができない場合に便利です。

# 例

```julia
# 以下はMermaidライブエディタに貼り付けることができます：
# https://mermaid.live/

@aagent FreeAgent struct AgentType1 end
base = FreeAgent("agent1")
entangle!(base, AgentType1("agent2"))
entangle!(base, AgentType1("agent3"))

# UUIDを印刷しない
hierarchy = agent_hierarchy_mmd(base)
print(join(hierarchy,""))

# UUIDの最後の4桁を印刷する
hierarchy = agent_hierarchy_mmd(base, use_uuid = 4)
print(join(hierarchy,""))
```
