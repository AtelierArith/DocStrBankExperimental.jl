```
@widen(typetag, types)
```

型タグに対応する型のセットを `types` を含むように拡張します。ここで `types` は単一の型またはセットコンストラクタに渡すことができる任意のコレクションです。型タグはモジュール修飾シンボル `mod.:Key` であり、ここで `mod` はモジュールを指定し、`:Key` はシンボルです。もし `:Key` のみが与えられた場合、モジュールはマクロが展開されたモジュールであると仮定されます。具体化が存在しない場合、ロード時に `Key` という名前を共有する任意の型の具体的なサブタイプからなるデフォルトの具体化を作成します。

もし `@widen` が `@replicable` コードブロックによって参照された型タグに対して呼び出された場合、そのコードブロックは新しい具体化を反映するためにさらに複製されます。

# 例

```julia-repl
julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @replicable println(@hyperspecialize(BestInts))
Int32
Int64

julia> @widen BestInts (Bool, Int32, UInt128)
Bool
UInt128
Set(Type[Bool, UInt128, Int32, Int64])

julia> @concretization BestInts
Set(Type[Bool, Int8, Int32, Int64, UInt128])
```
