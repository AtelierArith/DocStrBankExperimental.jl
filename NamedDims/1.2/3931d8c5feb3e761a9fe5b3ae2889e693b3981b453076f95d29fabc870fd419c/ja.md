```
NamedDimsArray{L, T, N, A}(data)
```

`NamedDimsArray`は、元の配列へのビューを提供するラッパー配列型であり、次元を位置ではなく名前で参照することができます。

例えば：

```
xs = NamedDimsArray{(:features, :observations)}(data);

n_obs = size(xs, :observations)
feature_totals = sum(xs; dims=:observations)

first_obs_vector = xs[observations=1]
x = x[observations=15, features=2]  # 15番目の観測における2番目の特徴。
```

`NamedDimsArray`は通常、（ほぼ）ゼロコストの抽象化です。一般的に、次元名に関連するほとんどの操作はコンパイル時に解決されます。

`NamedDimsArray`コンストラクタは、次元ごとに1つの`Symbol`として名前のリストとラップする配列を受け取ります。ラップされる配列がすでに`NamedDimsArray`である場合、新しい名前は既存の名前と組み合わされ、ワイルドカード（`:_`）を置き換えます。新しい名前が古い名前と互換性がない場合（すなわち、非ワイルドカードが一致しない場合）にはエラーが発生します。古い名前との互換性を考慮せずに`NamedDimsArray`に新しい名前を割り当てるには、`rename`(@ref)を参照してください。
