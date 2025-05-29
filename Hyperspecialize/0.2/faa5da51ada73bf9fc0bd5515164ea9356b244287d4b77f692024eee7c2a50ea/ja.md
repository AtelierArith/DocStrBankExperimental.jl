```
@replicable block
```

`block`内のコードを複製し、`@hyperspecialize(typetag)`によって参照される各タイプタグは、`typetag`の具体化の要素に置き換えられます。`block`は、`@replicable`が展開されたモジュールのグローバルスコープで、各`typetag`の具体化の各タイプの組み合わせごとに一度複製されます。タイプタグは、モジュールを指定するシンボル`mod.:Key`であり、ここでmodはモジュールを指定し、`:Key`はシンボルです。`:Key`のみが指定された場合、モジュールはマクロが展開されたモジュールであると見なされます。タイプタグに対する具体化が存在しない場合は、ロード時に`Key`という名前を共有する任意のタイプの具体的なサブタイプからなるデフォルトの具体化を作成します。

`@widen`が`@replicable`コードブロックによって参照されたタイプタグに対して呼び出されると、そのコードブロックは新しい具体化を反映するためにさらに複製されます。

# 例

```julia-repl
julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @replicable println(@hyperspecialize(BestInts), @hyperspecialize(BestInts))
Int32Int32
Int32Int64
Int64Int32
Int64Int64

julia> @widen BestInts (Bool,)
BoolBool
BoolInt32
BoolInt64
Int32Bool
Int64Bool
Set(Type[Bool, Int32, Int64])
```
