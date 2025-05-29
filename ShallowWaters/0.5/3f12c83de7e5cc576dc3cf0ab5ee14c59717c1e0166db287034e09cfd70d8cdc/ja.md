```
u,v,η,sst = run_model()
```

は、src/DefaultParameters.jlで定義されたデフォルトパラメータを使用してShallowWatersを実行します。

# 例

```jldoc
julia> u,v,η,sst = run_model(Float64,nx=200,output=true)
```
