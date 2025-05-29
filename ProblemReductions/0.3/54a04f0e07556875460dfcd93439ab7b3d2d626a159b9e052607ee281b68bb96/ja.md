```
num_flavors(::Type{<:AbstractProblem}) -> Int
num_flavors(::GT) where GT<:AbstractProblem -> Int
```

自由度のフレーバー（ドメイン）の数を返します。
