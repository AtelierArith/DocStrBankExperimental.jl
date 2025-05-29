```
reset_uniquename!(counter=GLOBAL_NAME_COUNTER)
```

すべての文字列の[`uniquename`](@ref)カウンタをリセットします。

`counter`は、各名前がどれだけ見られたかをカウントする`Dict{String,Int}`です。デフォルトは、`uniquename`で使用される同じデフォルトのグローバルカウンタです。
