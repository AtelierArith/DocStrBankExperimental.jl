```
Subpixel(ap, N=1) <: AbstractAperture
```

正確な幾何学的方法の代わりに、ピクセルシェーディングのためにサブピクセルの数値近似を使用します。

`ap`の境界にある任意のピクセルに対して、シェーディングアルゴリズムは境界ピクセルを`(N, N)`サブピクセルに分割することによって変更されます。シェーディング値は、`ap`の幾何学的境界内にあるこれらのサブピクセルの割合です。

サブピクセルシェーディング法は、正確な方法よりも速い場合がありますが、精度が犠牲になります。 [`CircularAperture`](@ref)の場合、サブピクセル法は`N` ~ 7のときのみ正確な方法よりも速くなります。 [`EllipticalAperture`](@ref)の場合、カットオフは`N` ~ 12であり、[`RectangularAperture`](@ref)の場合、カットオフは`N` ~ 20です。

# 例

```jldoctest
julia> ap = CircularAperture(3, 3, 2.5)
5×5 CircularAperture{Float64} with indices 1:5×1:5:
 0.136857  0.769325  0.983232  0.769325  0.136857
 0.769325  1.0       1.0       1.0       0.769325
 0.983232  1.0       1.0       1.0       0.983232
 0.769325  1.0       1.0       1.0       0.769325
 0.136857  0.769325  0.983232  0.769325  0.136857

julia> sub_ap = Subpixel(ap, 5)
5×5 Subpixel{Float64, CircularAperture{Float64}} with indices 1:5×1:5:
 0.12  0.76  1.0  0.76  0.12
 0.76  1.0   1.0  1.0   0.76
 1.0   1.0   1.0  1.0   1.0
 0.76  1.0   1.0  1.0   0.76
 0.12  0.76  1.0  0.76  0.12
```

!!! note
    `photutils`は、1つのサブピクセルを使用した`Subpixel`メソッドと同等の`center`シェーディングメソッドを提供します。不要な名前空間の混乱を避けるために、ユーザーには`Subpixel(ap)`を使用するように指示します。

