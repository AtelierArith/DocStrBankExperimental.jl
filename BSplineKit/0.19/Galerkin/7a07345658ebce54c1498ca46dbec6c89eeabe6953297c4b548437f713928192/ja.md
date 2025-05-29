```
galerkin_tensor(
    B::AbstractBSplineBasis,
    (D₁::Derivative, D₂::Derivative, D₃::Derivative),
    [T = Float64],
)
```

3Dバンデッドテンソルを計算します。これは、ガレルキン法における二次項から現れます。

[`galerkin_matrix`](@ref)と同様に、`B`の代わりに3つの`AbstractBSplineBasis`のタプル`(B₁, B₂, B₃)`を渡すことで、異なる関数基底を組み合わせることも可能です。現時点では、最初の2つの基底`B₁`と`B₂`は同じ長さでなければなりません。

テンソルは、[`BandedTensor3D`](@ref)オブジェクトに効率的に格納されます。
