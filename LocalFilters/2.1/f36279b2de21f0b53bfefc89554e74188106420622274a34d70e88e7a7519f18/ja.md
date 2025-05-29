LocalFilters.centered_offset(len)

は、長さ `len` の中心に沿った次元のインデックスオフセットを返します。つまり、`-div(Int(len)+2,2)` です。偶数の次元長の場合、これは `fftshift` と同じ規則を使用することになります。

[`LocalFilters.kernel_range`](@ref) と [`LocalFilters.centered`](@ref) を参照してください。
