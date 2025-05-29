```
CSGGenerator{T<:Real}
```

これは、CSGオブジェクトを作成する際に使用すべき型です。この型は、異なる変換を持つ[`CSGTree`](@ref)オブジェクトの構築を可能にします。ジェネレーターが評価されると、すべての変換が[`LeafNode`](@ref)sに伝播され、そこに保存されます。

# 例

```julia
a = Cylinder(1.0,1.0)
b = Plane([0.0,0.0,1.0], [0.0,0.0,0.0])
generator = a ∩ b
# これで、レイトレース可能なcsgオブジェクトを作成します
csgobj = generator(Transform(1.0,1.0,2.0))
```
