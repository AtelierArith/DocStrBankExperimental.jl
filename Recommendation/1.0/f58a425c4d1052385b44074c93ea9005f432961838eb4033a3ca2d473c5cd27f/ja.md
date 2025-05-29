```
count_users_contain(item::Integer, recommendations::AbstractVector{<:AbstractVector{<:Integer}}) -> Int
```

複数のユーザーに対するトップ-k 推薦リストの配列が与えられたとき、特定のアイテム `item` が推薦されたユーザーの数をカウントします。
