```
Spin <: QSym
```

[`SpinSpace`](@ref)を表すスピン演算子で、集合スピンシステムのためのスピン演算子Sx、Sy、Szを表します。フィールド軸はそれぞれx、y、zを1、2、3として表します。演算子は角運動量演算子のルールに従います: [Sj,Sk] = i⋅∑ϵjkl⋅Sl

# 例

```
julia> h = SpinSpace("Spin-N/2")
ℋ(Spin-N/2)

julia> Sx = Spin(h,:S,1)
Sx
```
