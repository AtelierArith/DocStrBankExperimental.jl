```
updaterun(instance::MLFlow, run_id::String; status::Union{RunStatus, Missing}=missing,
    end_time::Union{Int64, Missing}=missing, run_name::Union{String, Missing}=missing)
updaterun(instance::MLFlow, run::Run; status::Union{RunStatus, Missing}=missing,
    end_time::Union{Int64, Missing}=missing, run_name::Union{String, Missing}=missing)
```

[`Run`](@ref) メタデータを更新します。

# 引数

  * `instance`: [`MLFlow`](@ref) 設定。
  * `run_id`: 更新する [`Run`](@ref) の ID。
  * `status`: 更新された [`Run`](@ref) のステータス。
  * `end_time`: [`Run`](@ref) が終了した時のミリ秒単位の Unix タイムスタンプ。
  * `run_name`: 更新された [`Run`](@ref) の名前。

# 戻り値

  * 更新されたメタデータを持つ [`RunInfo`](@ref) 型のインスタンス。
