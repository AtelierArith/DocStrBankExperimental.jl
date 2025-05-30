```
cat_reorder(cat_var::AbstractVector, order_var::AbstractVector, fun::String, desc::Bool=true)
```

別の変数から計算された要約統計に基づいて、カテゴリ変数列のレベルを再順序付けします。

引数 `cat_var`: 再順序付けするカテゴリ変数列。 `order_var`: 要約統計を計算するための変数。 `fun`: 要約統計を計算するための関数。オプションは「mean」と「median」です。 `desc`: trueの場合、レベルは要約統計の降順で並べられます。

# 戻り値

レベルが再順序付けされたカテゴリ配列。

# 例

```jldoctest
julia> cat_var = String["A", "B", "A", "B", "A", "B", "C", "C", "C"];
       order_var = [1, 2, 3, 4, 5, 6, 7, 8, 9];
       cat_reorder(cat_var, order_var, "mean")
9-element CategoricalArrays.CategoricalArray{String,1,UInt32}:
 "A"
 "B"
 "A"
 "B"
 "A"
 "B"
 "C"
 "C"
 "C"
```
