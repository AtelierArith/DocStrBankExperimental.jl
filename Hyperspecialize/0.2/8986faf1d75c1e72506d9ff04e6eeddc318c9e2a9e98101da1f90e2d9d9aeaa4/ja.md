```
@concretize(typetag, types)
```

型タグに対応する型の集合を `types` と定義します。ここで、`types` は単一の型またはセットコンストラクタに渡すことができる任意のコレクションです。型タグはモジュール修飾シンボル `mod.:Key` であり、ここで `mod` はモジュールを指定し、`:Key` はシンボルです。もし `:Key` のみが与えられた場合、モジュールはマクロが展開されたモジュールであると仮定されます。

他のモジュールで型を具現化することはできないことに注意してください。

# 例

```julia-repl
julia> @concretize Main.BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @concretize BestFloats Float64
Set(Type[Float64])

julia> @concretize BestStrings (String,)
Set(Type[String])

julia> @concretization BestInts
Set(Type[Int32, Int64])
```
