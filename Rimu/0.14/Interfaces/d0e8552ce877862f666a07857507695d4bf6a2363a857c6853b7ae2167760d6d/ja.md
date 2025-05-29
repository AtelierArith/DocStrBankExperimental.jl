```
offdiagonals(h::AbstractHamiltonian, address)
```

`address`と同じ列にある`h`の非ゼロオフダイアゴナル行列要素のイテレータを返します。ペア`(newaddress, matrixelement)`をイテレートします。

# 例

```jldoctest
julia> address = BoseFS(3,2,1);


julia> H = HubbardReal1D(address);


julia> h = offdiagonals(H, address)
6-element Rimu.Hamiltonians.Offdiagonals{BoseFS{6, 3, BitString{8, 1, UInt8}}, Float64, HubbardReal1D{Float64, BoseFS{6, 3, BitString{8, 1, UInt8}}, 1.0, 1.0}}:
 (fs"|2 3 1⟩", -3.0)
 (fs"|2 2 2⟩", -2.449489742783178)
 (fs"|3 1 2⟩", -2.0)
 (fs"|4 1 1⟩", -2.8284271247461903)
 (fs"|4 2 0⟩", -2.0)
 (fs"|3 3 0⟩", -1.7320508075688772)
```

[`AbstractHamiltonian`](@ref)インターフェースの一部です。

# 拡張ヘルプ

`offdiagonals`は`<:AbstractOffdiagonals`型のイテレータを返します。デフォルトでは`Offdiagonals(h, a)`を返します。

[`Offdiagonals`](@ref Main.Hamiltonians.Offdiagonals)、[`AbstractOffdiagonals`](@ref Main.Hamiltonians.AbstractOffdiagonals)も参照してください。
