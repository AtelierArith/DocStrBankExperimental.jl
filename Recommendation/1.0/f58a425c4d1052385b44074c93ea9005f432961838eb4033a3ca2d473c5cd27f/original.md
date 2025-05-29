```
count_users_contain(item::Integer, recommendations::AbstractVector{<:AbstractVector{<:Integer}}) -> Int
```

Given an array of top-k recommendation lists for multiple users, count the number of users who are recommended a particular item `item`.
