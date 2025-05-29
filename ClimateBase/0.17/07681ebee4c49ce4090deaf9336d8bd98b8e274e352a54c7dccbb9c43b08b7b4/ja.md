```
value_space(A, B, C; Arange, Brange) → Cmeans, bin_indices
```

配列 `C` を `A, B` の共通値空間に表現します。`A, B, C` は同じインデックスを持たなければなりません。

与えられた範囲に基づいて2Dヒストグラムが作成され、`C` の要素は `A, B` の値に従ってビン分けされます。次に、要素が平均化され、共通空間 S = `Arange × Brange` 上で定義された行列 `Cmeans` が返されます。`bin_indices` も行列です（ベクトル要素を持つ）。`Cmeans` は要素がないビンに対して `NaN` になります。
