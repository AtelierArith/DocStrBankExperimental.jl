```
run_model_from_checkpoint(filename)
```

チェックポイントからモデルを実行します。`filename`はチェックポイントへのパスです。高度なモードを使用しているときのみ実行してください。データは以前と同じパスにある必要があります。

# 例:

```julia
julia> dp = run_model_from_checkpoint("checkpoint__50.jld2")
Loading Model:
  1.073261 seconds (2.27 M allocations: 113.221 MiB, 2.60% gc time)
Including params
Loading data:
  0.000881 seconds (10.02 k allocations: 378.313 KiB)
Creating model:
Node Leaders:
Dict{Any,Any}(2=>Any[2, 3])
Running model:
...
```
