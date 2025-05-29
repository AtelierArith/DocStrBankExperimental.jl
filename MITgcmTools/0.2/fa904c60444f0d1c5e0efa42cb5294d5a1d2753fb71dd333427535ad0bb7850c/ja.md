```
MITgcm_config()
```

`MITgcm`の`AbstractModelConfig`の具象型（`MITgcm`のための`ClimateModels.jl`インターフェースの一部）で、以下を含みます。

```
    model :: String = "MITgcm"
    configuration :: String = ""
    options :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    inputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    outputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    status :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
    channel :: Channel{Any} = Channel{Any}(10) 
    folder :: String = tempdir()
    ID :: UUID = UUIDs.uuid4()
```

キーワードを使用して次のように構築できます。

```
unknown_config=MITgcm_config(configuration="unknown")
```
