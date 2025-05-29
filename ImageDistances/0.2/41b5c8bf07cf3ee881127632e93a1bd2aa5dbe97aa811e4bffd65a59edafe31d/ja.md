```
Hausdorff <: GenericHausdorff
hausdorff(x::BoolImage, y::BoolImage)
```

2つの点集合 $\mathcal{A}$ と $\mathcal{B}$ の間のハウスドルフ距離であり、これはそれぞれ `x` と `y` の1の点位置から構成されます。この距離は次の式を使用して計算されます：

$$
    \text{hausdorff}(x,y) = max(d(\mathcal{A}, \mathcal{B}), d(\mathcal{B}, \mathcal{A}))
$$

ここで

$$
    d(\mathcal{A}, \mathcal{B}) = max_{a\in\mathcal{A}}d(a, \mathcal{B}) \\
    d(a, \mathcal{B}) = max_{b\in\mathcal{B}}d(a, b)
$$

点間距離は [`Euclidean`](@ref) 距離を使用して計算されます。

## 参考文献

Dubuisson, M-P; Jain, A. K., 1994. *A Modified Hausdorff Distance for Object-Matching*.

参照： [`modified_hausdorff`](@ref)
