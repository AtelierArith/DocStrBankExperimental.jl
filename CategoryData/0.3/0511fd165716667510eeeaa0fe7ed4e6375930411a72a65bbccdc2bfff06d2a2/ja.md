```
macro objectnames(category, names)
```

カテゴリ名とそのオブジェクトを定義し、整形表示機能を提供します。

# 例

```julia
@objectnames PMFC{2,1,0,1,0,0} 0 1 # カテゴリ名なしで
@objectnames Fib = UFC{2,1,0,2,0} I τ # カテゴリ名ありで
```
