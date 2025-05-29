```
StatsStep{Alias, F<:Function, ById}
```

[`AbstractStatsProcedure`](@ref) のステップの仕様。`StatsStep` のインスタンスは呼び出し可能です。

# パラメータ

  * `Alias::Symbol`: 見栄えを良くするための型のエイリアス。
  * `F<:Function`: `StatsStep` によって `F.instance` で呼び出される関数の型。
  * `ById::Bool`: 複数の [`StatsSpec`](@ref) からの引数を `object-id` または `isequal` でグループ化するかどうか。

# メソッド

```
(step::StatsStep{A,F})(ntargs::NamedTuple; verbose::Union{Bool,IO}=false)
```

`ntargs` から [`groupargs`](@ref) と [`combinedargs`](@ref) を介して抽出された引数で、型 `F` の関数のインスタンスを呼び出します。

キーワード `verbose` が `true` の値を取るか、`ntargs` に `verbose=true` のキーと値のペアが含まれている場合、`StatsStep` の名前を含むメッセージが `stdout` に印刷されます。代替の `IO` ストリームは、`verbose` の値を設定することで指定できます。両方が指定された場合、`ntargs` からの値がキーワード引数を上書きします。

## 戻り値

  * `NamedTuple`: 名前付き中間結果。
