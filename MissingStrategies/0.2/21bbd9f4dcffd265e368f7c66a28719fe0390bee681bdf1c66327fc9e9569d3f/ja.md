```
handlemissings(fun, ...)
```

引数のeltypeでmissingを許可する新しいメソッドを定義する式を作成します。

# 引数

  * `fun`: 拡張する関数の式
  * `pos_missing = 1`: missingを処理する引数の位置
  * `pos_strategy = pos_missing + 1`: 関数シグネチャにMissingStrategyの引数を挿入する位置
  * `type_missing = :Any`: missingを処理する引数の新しい型。この値の式であることができます。
  * `defaultstrategy::Union{Nothing,MissingStrategy} = :nothing`: 戦略引数のデフォルト値。デフォルト値を指定しないことを示すには`:nothing`を使用します。この値の式であることができます。
  * `gens = ()`: ジェネレータ関数のタプル（[mgen]{@ref}を参照）
  * `argname_strategy = :ms`: 戦略引数の引数名のシンボル
  * `suffix="_hm"`: メソッドの曖昧さを避けるためにディスパッチ関数の名前に付加されます

通常、この関数は適切なデフォルト値を提供するマクロから呼び出されます。

  * [`@handlemissings_typed`](@ref) 元のメソッドの型がmissing値を許可しない場合に適しています
  * [`@handlemissings_any`](@ref) 元のメソッドの型がmissing値を許可する場合に適しています。
  * [`@handlemissings_stub`](@ref) ユーザー指定の処理ルーチンを書くために適しています。
