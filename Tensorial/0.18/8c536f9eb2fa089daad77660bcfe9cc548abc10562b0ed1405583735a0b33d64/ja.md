`Quaternion` は $q_w + q_x \bm{i} + q_y \bm{j} + q_z \bm{k}$ を表します。スカラー部分とベクトル部分はそれぞれ `q.scalar` と `q.vector` でアクセスできます。

# 例

```jldoctest
julia> Quaternion(1,2,3,4)
1 + 2𝙞 + 3𝙟 + 4𝙠

julia> Quaternion(1)
1 + 0𝙞 + 0𝙟 + 0𝙠

julia> Quaternion(Vec(1,2,3))
0 + 1𝙞 + 2𝙟 + 3𝙠
```

詳細は [`quaternion`](@ref) を参照してください。

!!! note
    `Quaternion` は実験的であり、将来のバージョンの Tensorial で変更されるか、消える可能性があります。

