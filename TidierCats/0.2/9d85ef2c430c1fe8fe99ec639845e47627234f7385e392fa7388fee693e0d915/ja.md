```
cat_expand(cat_array::CategoricalArray, new_levels...; after=Inf)
```

指定された位置に新しいレベルを追加することで、カテゴリカル配列のレベルを拡張します。

# 引数

  * `cat_array`: レベルを拡張するカテゴリカル配列
  * `new_levels`: カテゴリカル配列に追加される新しいレベル
  * `after`: 新しいレベルを挿入する位置。デフォルトはInfで、新しいレベルを最後に追加します。

# 戻り値

新しいレベルが追加されたカテゴリカル配列。

# 例

```julia
julia> cats = CategoricalArray(["a", "b", "c", "a", "c", "b"]);

julia> println("Original levels: ", levels(cats))
Original levels: ["a", "b", "c"]

julia> cats = cat_expand(f, "d", "e", "f");

julia> println("Expanded levels: ", levels(cats))
Expanded levels: ["a", "b", "c", "d", "e", "f"]
```
