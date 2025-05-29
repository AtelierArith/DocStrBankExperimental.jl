```
MITgcm_config()
```

Concrete type of `AbstractModelConfig` for `MITgcm` (as part of the `ClimateModels.jl` interface for `MITgcm`) which contains

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

and can be constructed using keywords as follows

```
unknown_config=MITgcm_config(configuration="unknown")
```
