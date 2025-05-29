```
struct ModelConfig <: AbstractModelConfig
```

Generic data structure for a model configuration. This serves as :

  * default concrete type for `AbstractModelConfig`
  * keyword constructor for `AbstractModelConfig`

```
model :: Union{Function,String,Pkg.Types.PackageSpec} = "anonymous"
configuration :: Union{Function,String} = "anonymous"
inputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
outputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
channel :: Channel{Any} = Channel{Any}(10) 
folder :: String = tempdir()
ID :: UUID = UUIDs.uuid4()
```
