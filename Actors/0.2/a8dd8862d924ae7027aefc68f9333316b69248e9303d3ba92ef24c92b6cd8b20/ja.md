```
checkpointing(level=1, filename::AbstractString=""; kwargs...)
```

チェックポイントアクターを開始し、それへの[`Link`](@ref)を返します。

# 引数

  * `filename::AbstractString`: アクターがチェックポイントバッファを保存すべきファイル名、
  * `on::Bool=false`: チェックポイントが自動的に更新され保存されるべきか、
  * `update::Int=10`: 更新間隔（秒）≥ 1、
  * `save::Int=60`: 保存間隔（秒）≥ 1、
  * `kwargs...`: [`spawn`](@ref)へのキーワード引数。

!!! note
    更新または保存は、その間隔が≥ 1秒である場合にのみ自動的に行われます。

