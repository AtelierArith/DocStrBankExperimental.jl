```
(pd2::PeriodicDistance2)(x, y=nothing, ofsx=nothing, ofsy=nothing; fromcartesian=false, ofs=nothing)
```

点 `x` と `y` の間の二乗周期距離。オプションでそれぞれのオフセット `ofsx` と `ofsy` を指定できます。周期距離は、入力のすべての周期的な画像の間の最短距離です。`x` と `y` が分数座標の三重項として与えられる場合、`ofsx` と `ofsy` に整数オフセットを入れても効果はありません。

`y` が設定されていない場合、原点との間の周期距離を計算します。

`fromcartesian` が設定されている場合、入力はデカルト座標で与えられなければなりません。そうでない場合、入力は分数座標で与えられていると仮定されます。

`ofs` が整数の可変ベクトル（StaticArrays.jl の `MVector{3,Int}` を推奨）に設定されている場合、`y .+ ofsy` の変換のオフセットが `x .+ ofsx` に対して `ofs` に格納されます。これは、返される周期距離が `y .+ ofsy .+ ofs` と `x .+ ofsx` の間の非周期距離に等しいことを意味します（分数座標を仮定）。オフセットは常に整数の三重項として返されますが、入力は `fromcartesian` が設定されている限りデカルト座標で与えることができます。

!!! warning
    この関数は `pd2` の内部状態を変更するため、スレッドセーフではありません。


## 例

```jldoctest
julia> mat = [26.04 -7.71 -8.32; 0.0 32.72 -3.38; 0.0 0.0 26.66];

julia> pd2 = PeriodicDistance2(mat)
PeriodicDistance2([26.04 -7.71 -8.32; 0.0 32.72 -3.38; 0.0 0.0 26.66])

julia> sqrt(pd2([0.5, 0, 0])) # a 軸の中点までの距離は単に a/2
13.02

julia> ofs = MVector{3,Int}(undef);

julia> vec1 = [0.9, 0.6, 0.5]; vec2 = [0.0, 0.5, 0.01];

julia> d2 = pd2(vec1, vec2; ofs)
210.57932044000003

julia> println(ofs) # vec2 が vec1 に最も近い画像を持つためのオフセット
[1, 0, 1]

julia> norm(mat*(vec2 .+ ofs .- vec1))^2 ≈ d2
true

julia> pd2(mat*vec1, mat*vec2; fromcartesian=true) ≈ d2
true
```
