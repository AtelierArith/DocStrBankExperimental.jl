```
convert_to_tensor(o::Union{PyObject, Number, Array{T}, Missing, Nothing}; dtype::Union{Type, Missing}=missing) where T<:Number
convert_to_tensor(os::Array, dtypes::Array)
```

入力 `o` をテンソルに変換します。もし `o` がすでにテンソルであり、`dtype`（提供されている場合）が `o` の型と同じであれば、演算子は何もしません。それ以外の場合、`convert_to_tensor` は数値配列を定数テンソルに変換するか、データ型をキャストします。`convert_to_tensor` は複数のテンソルも受け入れます。

# 例

```julia
convert_to_tensor([1.0, constant(rand(2)), rand(10)], [Float32, Float64, Float32])
```
