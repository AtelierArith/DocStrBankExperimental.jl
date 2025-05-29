```
Quaternion{T<:Number} <: Number
```

要素の型が `T` の四元数型。

`QuaternionF16`、`QuaternionF32` および `QuaternionF64` はそれぞれ `Quaternion{Float16}`、`Quaternion{Float32}` および `Quaternion{Float64}` のエイリアスです。 また、[`Rotor`](@ref) および [`QuatVec`](@ref) も参照してください。

関数

```
quaternion(w, x, y, z)
quaternion(x, y, z)
quaternion(w)
```

指定された成分を持つ新しい四元数を作成します。引数 `w` はスカラー成分で、`x`、`y`、`z` は対応する「ベクトル」成分です。これらの引数のいずれかが欠けている場合、それはゼロに設定されます。返される四元数の型は入力引数から推論されるか、上記のように型パラメータ `T` を渡すことで指定できます。

定数 [`imx`](@ref)、[`imy`](@ref)、および [`imz`](@ref) は、複素数の `im` のように使用して新しい `Quaternion` オブジェクトを作成することもできます。

# 例

```jldoctest
julia> quaternion(1, 2, 3, 4)
1 + 2𝐢 + 3𝐣 + 4𝐤
julia> Quaternion{Float64}(1, 2, 3, 4)
1.0 + 2.0𝐢 + 3.0𝐣 + 4.0𝐤
julia> quaternion(1.0, 2.0, 3.0, 4.0)
1.0 + 2.0𝐢 + 3.0𝐣 + 4.0𝐤
julia> quaternion(2, 3, 4)
0 + 2𝐢 + 3𝐣 + 4𝐤
julia> quaternion(1)
1 + 0𝐢 + 0𝐣 + 0𝐤
```
