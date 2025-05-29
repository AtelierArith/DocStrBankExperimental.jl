```
ModifiedHausdorff <: GenericHausdorff
modified_hausdorff(x::BoolImage, y::BoolImage)
```

2つの点集合 $\mathcal{A}$ と $\mathcal{B}$ の間の修正ハウスドルフ距離で、これはそれぞれ `x` と `y` の1の点位置から構成されます。距離は次の式を使用して計算されます：

$$
    \text{modified_hausdorff}(x,y) = max(d(\mathcal{A}, \mathcal{B}), d(\mathcal{B}, \mathcal{A}))
$$

ここで

$$
    d(\mathcal{A}, \mathcal{B}) = \frac{1}{N_a}\sum_{a\in\mathcal{A}}d(a, \mathcal{B}) \\
    d(a, \mathcal{B}) = max_{b\in\mathcal{B}}d(a, b)
$$

点間距離は [`Euclidean`](@ref) 距離を使用して計算されます。

## 参考文献

Dubuisson, M-P; Jain, A. K., 1994. *A Modified Hausdorff Distance for Object-Matching*.

関連情報: [`hausdorff`](@ref)
