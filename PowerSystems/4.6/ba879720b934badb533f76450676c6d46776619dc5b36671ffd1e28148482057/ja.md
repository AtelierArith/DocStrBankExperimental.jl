```julia
to_json(
    sys::PowerSystems.System,
    filename::AbstractString;
    user_data,
    pretty,
    force,
    runchecks
)

```

システムをJSONファイルにシリアライズし、時系列をHDF5ファイルに保存します。

# 引数

  * `sys::System`: システム
  * `filename::AbstractString`: 書き込むファイル名

# キーワード引数

  * `user_data::Union{Nothing, Dict} = nothing`: 記録するオプションのメタデータ
  * `pretty::Bool = false`: JSONを整形して表示するかどうか
  * `force::Bool = false`: 既存のファイルを上書きするかどうか
  * `check::Bool = false`: システムの検証チェックを実行するかどうか

`check = true`の場合にスローされる例外については、[`check_component`](@ref)を参照してください。
