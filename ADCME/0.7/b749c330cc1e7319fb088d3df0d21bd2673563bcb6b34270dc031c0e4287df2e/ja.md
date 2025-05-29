```
set_shape(o::PyObject, s::Union{Array{<:Integer}, Tuple{Vararg{<:Integer, N}}}) where N
set_shape(o::PyObject, s::Integer...)
```

`o`の形状を`s`に設定します。`s`は`o`の実際の形状でなければなりません。この関数は、未知の次元を持つテンソルを具体的な次元を持つテンソルに変換するために使用されます。

# 例

```julia
a = placeholder(Float64, shape=[nothing, 10])
b = set_shape(a, 3, 10)
run(sess, b, a=>rand(3,10)) # OK 
run(sess, b, a=>rand(5,10)) # エラー
run(sess, b, a=>rand(10,3)) # エラー
```
