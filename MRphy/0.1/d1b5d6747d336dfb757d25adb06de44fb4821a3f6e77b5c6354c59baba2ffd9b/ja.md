```
TypeND(T,Ns) = Union{AbstractArray{<:T,Ns[1]}, AbstractArray{<:T,Ns[2]},...}
```

異なる次元の`Union`{`<:T`型配列}を作成するための糖衣構文。

# 使用法

*入力*:

  * `T::Type` (1,), ユニオンの基になる型。
  * `Ns::Array{Int64,1}` (# 異なる次元,), 希望する次元の配列。
