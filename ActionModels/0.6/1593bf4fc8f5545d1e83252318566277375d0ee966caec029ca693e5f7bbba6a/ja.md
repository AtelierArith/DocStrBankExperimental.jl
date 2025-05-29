```
premade_agent(model_name::String, config::Dict = Dict(); verbose::Bool = true)
```

プレメイドエージェントのリストからエージェントを作成します。

# 引数

  * 'model_name::String': プレメイドモデルの名前。'help'に設定すると、可能なモデル名のリストが返されます。
  * 'config::Dict = Dict()': エージェントのための設定を含む辞書、パラメータや設定など。
  * 'verbose::Bool = true': falseに設定すると、警告が非表示になります。
