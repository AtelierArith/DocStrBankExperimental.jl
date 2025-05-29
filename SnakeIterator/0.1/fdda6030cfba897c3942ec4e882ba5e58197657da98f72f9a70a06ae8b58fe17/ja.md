```
snake(arr)
```

与えられた2D配列 `arr` のスネーキングイテレータを作成します。つまり、配列を通して連続したS字型を形成するために偶数列を逆にトラバースします。行に沿ってスネークするには、`permutedims` を使って `arr` を変換します。

#### 簡単なケース

```jldoctest example1
julia> using SnakeIterator

julia> arr = reshape(1:16, 4, 4)
4×4 reshape(::UnitRange{Int64}, 4, 4) with eltype Int64:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> s = collect(snake(arr)); # コレクションに対してスネーク

julia> reshape(s, 4, 4) # 偶数列が逆になっていることに注意
4×4 Array{Int64,2}:
 1  8   9  16
 2  7  10  15
 3  6  11  14
 4  5  12  13
```

#### スネークされた行をループする

```jldoctest example1
julia> println([i for i in snake(permutedims(arr))]) # 行優先順で訪問
[1, 5, 9, 13, 14, 10, 6, 2, 3, 7, 11, 15, 16, 12, 8, 4]

```
