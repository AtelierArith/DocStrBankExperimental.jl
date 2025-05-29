```
value_space(A, B; Arange) → Bmeans, bin_indices
```

配列 `B` を `A` の値空間に表現します。`B` と `A` は同じインデックスを持たなければなりません。これは、`A` が指定された `Arange` に従ってビン分けされ、`A` をビン分けしたのと同じインデックスが `B` のビン分けにも使用されることを意味します。`i` 番目のビンには、`A` の値が ∈ [`Arange[i]`, `Arange[i+1]`) のデータが含まれます。各ビン内で、ビン分けされた `B` の値が平均化され、`Bmeans` が得られます。

`Arange` に含まれない `A` の要素はスキップされます。返される `bin_indices` は各ビン内のインデックスです（したがって、平均の重みは単に `length.(bin_indices)` です）。

デフォルトでは `Arange = range(minimum(A), nextfloat(maximum(A)); length = 100)` です。
