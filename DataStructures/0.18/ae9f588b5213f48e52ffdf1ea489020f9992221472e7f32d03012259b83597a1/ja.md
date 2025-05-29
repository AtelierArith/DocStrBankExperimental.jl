```
Stack{T}([blksize::Integer=1024])
```

Last In First Out (LIFO) アクセスのために型 `T` の要素を含む `Stack` オブジェクトを作成します。

# 例

```jldoctest
julia> s = Stack{Int}() # スタックを作成
Stack{Int64}(Deque [Int64[]])

julia> push!(s, 1) # アイテムをプッシュバック
Stack{Int64}(Deque [[1]])

julia> x = top(s) # 最初のアイテムを取得
1

julia> length(s)
1

julia> x = pop!(s) # 最初のアイテムを取得して削除
1

julia> length(s)
0
```
