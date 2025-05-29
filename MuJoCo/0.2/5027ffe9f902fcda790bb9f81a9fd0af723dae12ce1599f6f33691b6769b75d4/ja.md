```
mju_addToScl(res, vec, scl)
```

res = res + vec*scl を設定します。

# 引数

  * **`res::Vector{Float64}`** -> 可変サイズのベクトル。`res` はベクトルであるべきで、行列ではありません。`res` と vec は同じサイズである必要があります。
  * **`vec::Vector{Float64}`** -> 可変サイズのベクトル。`vec` はベクトルであるべきで、行列ではありません。res と `vec` は同じサイズである必要があります。定数。
  * **`scl::Float64`**
