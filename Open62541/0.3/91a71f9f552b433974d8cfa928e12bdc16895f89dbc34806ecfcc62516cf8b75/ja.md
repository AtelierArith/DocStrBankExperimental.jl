```
JUA_Variant
```

`JUA_Variant`オブジェクトを定義する可変構造体 - `UA_Variant`の同等物ですが、メモリはCではなくJuliaによって管理されます（以下の例外を参照）。`JUA_Variant`は、スカラーまたは配列形式で任意のデータ型を保持できます。

以下のコンストラクタメソッドが定義されています：

```
JUA_Variant()
```

空の`JUA_Variant`を作成します。これは`UA_Variant_new()`を呼び出すのと同等です。

```
JUA_Variant(value::Union{T, AbstractArray{T}}) where T <: Union{UA_NUMBER_TYPES, AbstractString, ComplexF32, ComplexF64, Rational{<:Integer}})
```

`value`を含む`JUA_Variant`を作成します。バリアントのすべてのプロパティは自動的に設定されます。たとえば、`value`が配列である場合、arrayDimensionsおよびarrayDimensionsSizeプロパティは、`value`に含まれる各次元の次元数と要素数に基づいて設定されます。

```
JUA_Variant(variantptr::Ptr{UA_Variant})
```

ポインタ`variantptr`に基づいて`JUA_Variant`を作成します。これは、低レベルインターフェースを介して生成された`UA_Variant`を高レベル関数に渡すために使用できるフォールバックメソッドです。このメソッドを使用する際は、メモリ管理はC側に残ることに注意してください。つまり、オブジェクトがもはや必要ない場合、`variantptr`は手動で`UA_Variant_delete(variantptr)`でクリーンアップする必要があります。これを保証するのはユーザーの責任です。

例：

```
j = JUA_Variant()
j = JUA_Variant("私は文字列の値です")
j = JUA_Variant(["文字列1", "文字列2"])
j = JUA_Variant(rand(Float32, 2, 3, 4))
j = JUA_Variant(rand(Int32, 2, 2))
j = JUA_Variant(rand(ComplexF64, 8))
```
