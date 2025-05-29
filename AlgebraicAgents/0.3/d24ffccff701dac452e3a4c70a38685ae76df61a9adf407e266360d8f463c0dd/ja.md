```
extract_agent
```

エージェントを動的システムのプロパティとして抽出します（エージェントによってラップされています）。

# 例

```julia
agent = extract_agent(params) # SciML統合用
agent = extract_agent(model, agent) # ABM統合用
```
