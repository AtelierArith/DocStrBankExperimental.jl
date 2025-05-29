```
StatsSpec{T<:AbstractStatsProcedure}
```

タイプ `T` の統計手続きの仕様。

`StatsSpec` のインスタンスは呼び出し可能で、そのフィールドは手続きを実行するために必要なすべての情報を提供します。仕様のオプションの名前を指定することができます。

# フィールド

  * `name::String`: 仕様の名前（指定されていない場合は `""` になります）。
  * `args::NamedTuple`: `T` の [`StatsStep`](@ref) に対する引数（`args` に見つからない場合はデフォルト値が `args` にマージされます）。

# メソッド

```
(sp::StatsSpec{T})(; verbose::Union{Bool,IO}=false, keep=nothing, keepall::Bool=false)
```

`args` に指定された引数でタイプ `T` の手続きを実行します。デフォルトでは、`T` に対する専用の結果オブジェクトが利用可能な場合はそれが返されます。そうでない場合は、最後の [`StatsStep`](@ref) によって返された最後の値が返されます。

## キーワード

  * `verbose::Union{Bool,IO}=false`: 各ステップの名前を呼び出されたときに `stdout` または指定された `IO` ストリームに印刷します。
  * `keep=nothing`: 返される追加オブジェクトの名前（`Symbol` 型）。
  * `keepall::Bool=false`: 各ステップによって返されたすべてのオブジェクトを返します。
