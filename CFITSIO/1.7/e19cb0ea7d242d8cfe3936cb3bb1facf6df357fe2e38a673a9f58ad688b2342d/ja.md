```
fits_resize_img(f::FITSFile, T::Type, naxis::Integer,
                sz::Union{Vector{<:Integer}, Tuple{Vararg{Integer}}})
```

`f`内の画像のサイズ、次元、およびオプションで要素タイプを変更します。新しい画像は要素タイプ`T`を持ち、サイズ`sz`の`naxis`次元の画像になります。新しい画像が既存のものより大きい場合、末尾にゼロパディングされます。新しい画像が小さい場合、既存の画像データは切り捨てられます。

!!! note
    このメソッドは要素を強制的に変換するのではなく、データを再解釈します。


# 例

```jldoctest
julia> f = fits_clobber_file(tempname());

julia> a = [1 2; 3 4];

julia> fits_create_img(f, a);

julia> fits_write_pix(f, a);

julia> fits_get_img_size(f)
2-element Vector{Int64}:
 2
 2

julia> fits_resize_img(f, [3,3]);

julia> fits_get_img_size(f)
2-element Vector{Int64}:
 3
 3

julia> b = similar(a, (3,3));

julia> fits_read_pix(f, b); b
3×3 Matrix{Int64}:
 1  4  0
 3  0  0
 2  0  0

julia> fits_resize_img(f, [4]);

julia> b = similar(a, (4,));

julia> fits_read_pix(f, b); b
4-element Vector{Int64}:
 1
 3
 2
 4
```
