```
new_seg = prune_segments(seg, rem_labels, diff_fn)
```

`rem_labels`にあるラベルを持つすべてのセグメントを削除し、それらを最小の`diff_fn`を持つ隣接セグメントで置き換えます。`rem_labels`はラベルの`Vector`です。

```
new_seg = prune_segments(seg, is_rem, diff_fn)
```

`is_rem`がtrueを返すすべてのセグメントを削除し、それらを最小の`diff_fn`を持つ隣接セグメントで置き換えます。

```
is_rem(label) -> Bool
```

ラベル`label`が削除されるべきであればtrueを返し、そうでなければfalseを返します。

```
d = diff_fn(rem_label, neigh_label)
```

削除されるラベルとその隣接ラベルとの間の差異測定です。`d`の型のオブジェクトに対して`isless`が定義されている必要があります。
