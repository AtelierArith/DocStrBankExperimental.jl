```
getexperimentbyname(instance::MLFlow, experiment_name::String)
```

[`Experiment`](@ref)のメタデータを取得します。

このエンドポイントは削除された実験を返しますが、アクティブな[`Experiment`](@ref)と削除された[`Experiment`](@ref)が同じ名前を持つ場合は、アクティブな[`Experiment`](@ref)を優先します。複数の削除された実験が同じ名前を持つ場合、APIはそのうちの1つを返します。

# 引数

  * `instance`: [`MLFlow`](@ref)の設定。
  * `experiment_name`: 関連する[`Experiment`](@ref)の名前。

# 戻り値

[`Experiment`](@ref)型のインスタンス。
