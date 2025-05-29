```
@concretize(typetag)
```

もし具体化が存在しない場合、`typetag` に対応する型の集合を、ロード時に `Key` という名前を共有する任意の型の具体的なサブタイプとして定義します。 `typetag` は型タグであり、モジュール修飾シンボル `mod.:Key` で、ここで `mod` はモジュールを指定し、`:Key` はシンボルです。もし単に `:Key` が与えられた場合、マクロが展開されたモジュールがモジュールと見なされます。

他のモジュールで型タグを具体化することはできないことに注意してください。

# 例

```julia-repl
julia> @concretization(Main.Real)
nothing

julia> @concretize(Main.Real)
Set(Type[BigInt, Bool, UInt32, Float64, Float32, Int64, Int128, Float16, UInt128, UInt8, UInt16, BigFloat, Int8, UInt64, Int16, Int32])

julia> @concretize BestInts [Int32, Int64]
Set(Type[Int32, Int64])

julia> @concretization BestInts
Set(Type[Int32, Int64])

julia> @concretize NotDefinedHere
ERROR: cannot create default concretization from type tag Main.NotDefinedHere: not defined.
```
