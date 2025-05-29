```
interp1(x::Union{Array{Float64, 1}, PyObject},v::Union{Array{Float64, 1}, PyObject},xq::Union{Array{Float64, 1}, PyObject})
```

は、線形補間を使用して特定のクエリポイントでの1次元関数の補間値を返します。ベクトル x にはサンプルポイントが含まれ、v には対応する値 v(x) が含まれています。ベクトル xq にはクエリポイントの座標が含まれています。

!!! info
    `x` は昇順にソートされている必要があります。


# 例

```julia
x = sort(rand(10))
y = constant(@. x^2 + 1.0)
z = [x[1]; x[2]; rand(5) * (x[end]-x[1]) .+ x[1]; x[end]]
u = interp1(x,y,z)
```
