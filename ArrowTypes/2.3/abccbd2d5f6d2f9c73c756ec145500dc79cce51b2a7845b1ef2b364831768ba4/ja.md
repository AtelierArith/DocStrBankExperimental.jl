```
ArrowTypes.fromarrow(::Type{T}, x::S) => T
```

インターフェースメソッドは、ネイティブの矢印型 `S` から構築されるカスタム型 `T` のための「デシリアライズフック」を提供します。`T` と `S` の型は、`ArrowTypes.ArrowType(::Type{T}) = S` で使用される定義に対応している必要があります。これは [`ArrowTypes.toarrow`](@ref) とペアになったメソッドです。

デフォルトの定義は `ArrowTypes.fromarrow(::Type{T}, x) = T(x)` であるため、カスタム型に対してこれが機能する場合、追加のオーバーロードは必要ありません。いくつかの `ArrowKind` は、`fromarrow` メソッドに対してわずかに異なるカスタムオーバーロードを許可しています：

  * `ListKind{true}`: `String` 型の場合、`fromarrow(::Type{T}, ptr::Ptr{UInt8}, len::Int) = ...` とオーバーロードして、`String` を具現化するのを避けることができます。
  * `StructKind`:

      * 個々のフィールドが別々の位置引数として渡される `fromarrow(::Type{T}, x...)` をオーバーロードできます。したがって、私のカスタム型 `Interval` に `first` と `last` の2つのフィールドがある場合、`ArrowTypes.fromarrow(::Type{Interval}, first, last) = ...` のようにオーバーロードします。デフォルトの実装は `ArrowTypes.fromarrow(::Type{T}, x...) = T(x...)` であるため、型がすでにコンストラクタで全ての引数を受け入れる場合、追加の `fromarrow` メソッドは必要ありません（デフォルトの構造体コンストラクタはこの動作を持っています）。
      * あるいは、`fromarrowstruct(::Type{T}, ::Val{fnames}, x...)` をオーバーロードすることもでき、ここで `fnames` は `x` の値に対応するフィールド名のタプルです。このアプローチは、シリアライザによって使用されるフィールドの順序に依存しない方法でデシリアライズを実装する必要がある場合に便利です。実装されると、`fromarrowstruct` は `StructKind` のデシリアライズにおいて `fromarrow` よりも優先されます。
