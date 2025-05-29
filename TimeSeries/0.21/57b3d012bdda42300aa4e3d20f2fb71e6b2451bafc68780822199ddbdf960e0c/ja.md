```
rename!(ta::TimeArray, colnames::Vector{Symbol})
rename!(ta::TimeArray, colname::Symbol)
rename!(ta::TimeArray, orig => new, ...)
rename!(f::Base.Callable, ta, colnametyp)
```

`TimeArray`の列をインプレースで名前変更します。

関連情報は[`rename`](@ref)を参照してください。

# 引数

  * `colnametyp`は関数`f`の入力タイプです。有効な値は`Symbol`または`String`です。
