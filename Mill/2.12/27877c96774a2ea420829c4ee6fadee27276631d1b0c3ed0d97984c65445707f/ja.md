```
catobs(ns...)
```

複数のノードをマージしてサンプル（観測）を1つにまとめ、可能であればその過程で適切に昇格させます。

`Base.cat`に似ていますが、サンプルが保存されている抽象的な「軸」に沿って連結します。

異なる数の引数や引数の型で繰り返し呼び出す場合は、コンパイル時間を節約するために `reduce(catobs, [ns...])` を使用してください。

# 例

```jldoctest
julia> catobs(ArrayNode(zeros(2, 2)), ArrayNode([1 2; 3 4]))
2×4 ArrayNode{Matrix{Float64}, Nothing}:
 0.0  0.0  1.0  2.0
 0.0  0.0  3.0  4.0

julia> n = ProductNode(t1=ArrayNode(randn(2, 3)), t2=BagNode(ArrayNode(randn(3, 8)), bags([1:3, 4:5, 6:8])))
ProductNode  3 obs
  ├── t1: ArrayNode(2×3 Array with Float64 elements)  3 obs
  ╰── t2: BagNode  3 obs
            ╰── ArrayNode(3×8 Array with Float64 elements)  8 obs

julia> catobs(n[1], n[3])
ProductNode  2 obs
  ├── t1: ArrayNode(2×2 Array with Float64 elements)  2 obs
  ╰── t2: BagNode  2 obs
            ╰── ArrayNode(3×6 Array with Float64 elements)  6 obs
```
