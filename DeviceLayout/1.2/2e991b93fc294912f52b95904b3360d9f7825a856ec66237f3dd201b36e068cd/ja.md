```
reset_uniquename!(str::String, counter=GLOBAL_NAME_COUNTER)
```

`str`の[`uniquename`](@ref)カウンタをリセットします。

`counter`は、各名前がどれだけ見られたかをカウントする`Dict{String,Int}`です。デフォルトは`uniquename`で使用される同じデフォルトのグローバルカウンタです。
