```
svd(o::PyObject, args...; kwargs...)
```

`TFSVD`構造体を返し、以下のデータ構造を保持します。

```julia
S::PyObject
U::PyObject
V::PyObject
Vt::PyObject
```

私たちは等式 $o = USV'$ を持っています。

# 例

```julia
A = rand(10,20)
r = svd(constant(A))
A2 = r.U*diagm(r.S)*r.Vt # `A2`の値は`A`と等しいはずです
```
