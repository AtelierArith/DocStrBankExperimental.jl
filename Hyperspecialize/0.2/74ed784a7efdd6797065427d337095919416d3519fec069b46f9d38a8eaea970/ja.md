```
@concretization(typetag)
```

型タグに対応する型のセットを返します。型タグは、モジュールを指定するシンボル `mod.:Key` であり、ここで mod はモジュールを指定し、`:Key` はシンボルです。`:Key` のみが指定された場合、モジュールはマクロが展開されたモジュールであると見なされます。具体化が存在しない場合は、何も返しません。

具体化は `@concretize` と `@widen` を使用して設定および変更できます。

# 例

```julia-repl
julia> @concretization(BestInts)
nothing

julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @concretization BestInts
Set(Type[Int32, Int64])
```
