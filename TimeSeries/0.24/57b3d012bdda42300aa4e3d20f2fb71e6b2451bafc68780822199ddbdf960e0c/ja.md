```
rename!(ta::TimeArray, colnames::Vector{Symbol})
rename!(ta::TimeArray, colname::Symbol)
rename!(ta::TimeArray, orig => new, ...)
rename!(f::Base.Callable, ta, colnametyp)
```

`TimeArray`の列をインプレースで名前変更します。

参照してください [`rename`](@ref)。

# 引数

  * `colnametyp` は関数 `f` の入力タイプです。有効な値は `Symbol` または `String` です。
