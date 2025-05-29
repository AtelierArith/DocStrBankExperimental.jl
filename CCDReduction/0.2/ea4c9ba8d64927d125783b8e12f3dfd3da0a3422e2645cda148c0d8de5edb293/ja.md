```
flat_correct(frame, flat_frame; norm_value = mean(flat_frame), [hdu = 1])
```

キャリブレーションされた `flat_frame` を使用して、非一様性に対して `frame` を補正します。

デフォルトでは、`flat_frame` はその平均で正規化されますが、カスタムの `norm_value` を提供することで変更できます。

どちらかが文字列の場合、それらは最初に [`CCDData`](@ref) に読み込まれます。読み込まれるHDUは、整数または各ファイルに対応するタプルとして `hdu` で指定できます。

!!! note
    この関数は、`flat_frame` に非常に近い値が含まれている場合、ゼロで割ることによって非有限値を導入する可能性があります。デフォルトの動作では、フレーム値が非ゼロの場合は `Inf` を返し、フレーム値が `0` の場合は `Nan` を返します。


# 例

```jldoctest
julia> frame = ones(3, 3);

julia> flat = fill(2.0, (3, 3));

julia> flat_correct(frame, flat, norm_value = 1.0)
3×3 Matrix{Float64}:
 0.5  0.5  0.5
 0.5  0.5  0.5
 0.5  0.5  0.5

julia> flat_correct(frame, flat)
3×3 Matrix{Float64}:
 1.0  1.0  1.0
 1.0  1.0  1.0
 1.0  1.0  1.0
```

# 参照

[`flat_correct!`](@ref)
