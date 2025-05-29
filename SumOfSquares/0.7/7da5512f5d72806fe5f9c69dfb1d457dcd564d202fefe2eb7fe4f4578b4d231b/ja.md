```
struct NonnegPolyInnerCone{MCT <: MOI.AbstractVectorSet}
end
```

非負多項式の円錐の内近似は、次の形式の多項式の集合によって定義されます。

```julia
X^\top Q X
```

ここで、`X` は単項式のベクトルであり、`Q` は円錐 `psd_inner` に属する対称行列です。
