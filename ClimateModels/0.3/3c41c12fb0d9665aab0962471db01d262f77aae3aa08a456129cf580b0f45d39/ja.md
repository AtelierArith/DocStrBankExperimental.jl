```
struct ModelConfig <: AbstractModelConfig
```

モデル構成のための汎用データ構造。これは以下の役割を果たします：

  * `AbstractModelConfig` のデフォルト具体型
  * `AbstractModelConfig` のキーワードコンストラクタ

```
model :: Union{Function,String,Pkg.Types.PackageSpec} = "anonymous"
configuration :: Union{Function,String} = "anonymous"
inputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
outputs :: OrderedDict{Any,Any} = OrderedDict{Any,Any}()
channel :: Channel{Any} = Channel{Any}(10) 
folder :: String = tempdir()
ID :: UUID = UUIDs.uuid4()
```
