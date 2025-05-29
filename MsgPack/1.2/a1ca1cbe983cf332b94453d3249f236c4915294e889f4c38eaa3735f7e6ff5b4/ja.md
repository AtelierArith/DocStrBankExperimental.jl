```
unpack(msgpack_byte_stream::IO, T::Type = Any; strict::Tuple=())
```

`msgpack_byte_stream` からデシリアライズされた型 `T` の Julia 値を返します。

`T` は有効な [`msgpack_type`](@ref) と [`from_msgpack`](@ref) 定義を持つと仮定されます。

もし `msgpack_type(T) === AnyType()` の場合、`unpack` は `msgpack_byte_stream` から次の MessagePack オブジェクトをデシリアライズし、そのオブジェクトの MessagePack 型に対応するデフォルトの Julia 表現に変換します。デフォルトの Julia 表現の詳細については、[`AbstractMsgPackType`](@ref) を参照してください。

`strict` キーワード引数は `DataType` の `Tuple` であり、各要素 `S` は `msgpack_type(S) === StructType()` に従わなければなりません。`unpack` は遭遇した MessagePack マップがデシリアライズされるとき、例えば `S` が常に `S` のフィールドに厳密に対応するフィールドを含むと仮定します。言い換えれば、マップの `i` 番目のキーは `fieldname(S, i)` に対応し、`i` 番目の値は `getfield(::S, i)` に対応しなければなりません。

関連情報: [`pack`](@ref), [`construct`](@ref)
