Unitful.jlを拡張して、角度を独立した次元として含めることで、[ディスパッチ](https://docs.julialang.org/en/v1/manual/methods/#Methods)を容易にします。

詳細については、[ドキュメント](https://cmichelenstrofer.github.io/DimensionfulAngles/)をご覧ください。

!!! note "非SI"
    *角度*はSI基本次元ではありません。


# 例

```jldoctest; filter = r"(\d*).(\d{1,10})\d+" => s"\1.\2"
julia> using DimensionfulAngles

julia> 1.0ua"turn"
1.0 τ

julia> 1.0ua"rad" - 1.0ua"°"
0.9825467074800567 rad

julia> cos(45ua"°")
0.7071067811865476
```
