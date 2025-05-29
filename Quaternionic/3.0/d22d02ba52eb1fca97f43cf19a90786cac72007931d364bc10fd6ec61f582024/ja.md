```
QuatVec{T<:Number} <: Number
```

要素の型が `T` の純ベクトルクォータニオン。これらのオブジェクトは、一般的な `Quaternion` よりも特定の操作において大幅に高速かつ正確である場合があります。

`QuatVecF16`、`QuatVecF32` および `QuatVecF64` はそれぞれ `QuatVec{Float16}`、`QuatVec{Float32}` および `QuatVec{Float64}` のエイリアスです。詳細は [`Quaternion`](@ref) および [`Rotor`](@ref) を参照してください。

関数

```
quatvec(w, x, y, z)
quatvec(x, y, z)
quatvec(w)
```

は、与えられた成分を持つ新しい `QuatVec` を作成します（成分は [`Quaternion`](@ref) に記載されている通りですが、スカラー引数 `w` は常に 0 に設定されます）。

# 例

```jldoctest
julia> quatvec(1, 2, 3, 4)
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(quaternion(1, 2, 3, 4))
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(2, 3, 4)
 + 2𝐢 + 3𝐣 + 4𝐤
julia> quatvec(1)
 + 0𝐢 + 0𝐣 + 0𝐤
```
