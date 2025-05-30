```
start_actor(start, sv, cb=nothing, restart::Symbol=:transient; 
            name::Union{Symbol,Nothing}=nothing, kwargs...)
```

スーパーバイザー `sv` にアクターを開始するよう指示し、それを子リストに追加し、そのリンクを返します。

# 引数

  * `start`: 子の開始動作、呼び出し可能なオブジェクト、
  * `sv::Link`: 開始されたスーパーバイザーへのリンク、
  * `cb=nothing`: コールバック（呼び出し可能なオブジェクトで、最後のアクターの動作を引数として受け取り、[`Link`](@ref) を返さなければならない）；`nothing` の場合、アクターはその [`init!`](@ref) コールバックまたは最後の動作で再起動されます、
  * `restart::Symbol=:transient`: [再起動オプション](@ref restart)、`:permanent`、`:temporary`、`:transient` のいずれか、
  * `name::Union{Symbol,Nothing}=nothing`: アクターが登録されるべき名前（シンボル）、
  * `kwargs...`: [`spawn`](@ref) へのキーワード引数。
