```
MITgcm_config()
```

`MITgcm`の`AbstractModelConfig`の具体的な型（`MITgcm`のための`ClimateModels.jl`インターフェースの一部）で、以下を含みます。

```
    model :: String = "MITgcm"
    configuration :: String = ""
    inputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    outputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    channel :: Channel{Any} = Channel{Any}(10) 
    folder :: String = tempdir()
    ID :: UUID = UUIDs.uuid4()
```

および、以下のようにキーワードを使用して構築できます。

```
unknown_config=MITgcm_config(configuration="unknown")
```
