```
dxy_dt_CyclicArray(du,u,P::NamedTuple,tim)
```

最近傍 (?) ベクトルはグリッド化されたフィールドから取得されます (2D; サイクリック配列を使用して有効なインデックス範囲を拡張するため、ハローは必要ありません)。

# 拡張ヘルプ

*注:* 空間補間と時間補間は不足しています

```jldoctest; output = false
using IndividualDisplacements
p=dirname(pathof(IndividualDisplacements))
include(joinpath(p,"../examples/more/example_CyclicArray.jl"))
(x,y)=cyclicarray_example()

ref=[330.5 290.5]
prod(isapprox.([x[end] y[end]],ref,atol=1.0))

# output

true
```
