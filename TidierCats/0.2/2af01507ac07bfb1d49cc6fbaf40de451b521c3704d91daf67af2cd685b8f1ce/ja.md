```
cat_recode(cat_array::Union{CategoricalArray, AbstractVector}; kwargs...)
```

提供されたマッピングに基づいて、カテゴリカル配列のレベルを再コーディングします。

# 引数

  * `cat_array`: 再コーディングするカテゴリカル配列
  * `kwargs`: 元のレベルをキー、新しいレベルを値とする辞書。キーにないレベルはそのまま保持されます。

# 戻り値

レベルが再コーディングされたカテゴリカル配列。

# 例

```jldoctest
julia> x = CategoricalArray(["apple", "tomato", "banana", "dear"]);

julia> println(levels(cat_recode(x, fruit = ["apple", "banana"], nothing = ["tomato"])))
["fruit", "nothing", "dear"]
```
