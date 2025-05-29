```
remove_segment!(seg, label, diff_fn)
```

ラベル `label` を持つセグメントをその隣接セグメントで置き換え、`diff_fn` 値が最も小さいものを使用してインプレースで削除します。

```
d = diff_fn(rem_label, neigh_label)
```

削除されるラベルとその隣接ラベルとの間の差異測定。`isless` は `d` の型のオブジェクトに対して定義されている必要があります。

# 例

```julia
    # これはラベル `l` を削除し、ピクセル数が最大の隣接ラベルで置き換えます。
    julia> remove_segment!(seg, l, (i,j)->(-seg.segment_pixel_count[j]))

    # これはラベル `l` を削除し、ユークリッド距離の値が最も小さい隣接ラベルで置き換えます。
    julia> remove_segment!(seg, l, (i,j)->sum(abs2, seg.segment_means[i]-seg.segment_means[j]))
```
