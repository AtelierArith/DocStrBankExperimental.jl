```
setinvalid_range!(df, var_ranges...; setvalmissing = true, ...)
```

指定された範囲外の値を持つレコードを :valid 列で false に設定します。

小さい値または大きい値に制限がない場合は、それぞれ最小値または最大値として `-Inf` または `Inf` を指定します。 :value 列に以前に false の値があった場合、それらは false のまま保持されます。さらに、範囲外の値を missing に設定します。

# 引数

  * `df`: 列 :GPP を持つ DataFrame
  * `var_ranges`: ペア `Varname_symbol => (min,max)`: 各列の閉じた有効区間

オプション

  * setvalmissing: false に設定すると、範囲外の値を持つ value 列の値を missing に置き換えるのを防ぎます。

# 値

修正された :valid および value 列を持つ df。

```jldoctest; output = false
using DataFrames
df = DataFrame(NEE = [missing, 2,3], GPP = 10:10:30)
setinvalid_range!(df, :NEE => (-2.0,4.0), :GPP => (8.0,28.0))
df.valid == [false, true, false]
ismissing(df.GPP[3])
# output
true
```
