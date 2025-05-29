LocalFilters.centered(A) -> B

抽象配列 `B` を生成し、配列 `A` のエントリを共有しますが、インデックスにオフセットを加えることで `B` の軸が *中心* に配置されます（偶数次元の長さの場合、`fftshift` と同じ規則が使用されます）。

この *public* メソッドは、混乱を招く可能性があるため、意図的にエクスポートされていません。例えば、`OffsetArrays.centered` は似ていますが、わずかに異なる意味を持っています。

さらに [`LocalFilters.kernel_range`](@ref) や [`LocalFilters.centered_offset`](@ref) も参照してください。
