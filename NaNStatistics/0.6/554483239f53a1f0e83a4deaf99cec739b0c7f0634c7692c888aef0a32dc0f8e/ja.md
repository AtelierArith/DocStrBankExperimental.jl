```julia
nanbinmedian!(M, [N], x, y, xedges::AbstractRange)
```

配列 `M` を、`x` 軸に沿った `length(xedges)-1` の等間隔のビンに落ちる非 NaN の `y` 値の中央値（オプションで `N` にカウントも）で埋めます。ビンの境界は `xedges` で指定されます。

`y` が 2 次元配列（行列）の場合、各列は別々の変数として扱われます。
