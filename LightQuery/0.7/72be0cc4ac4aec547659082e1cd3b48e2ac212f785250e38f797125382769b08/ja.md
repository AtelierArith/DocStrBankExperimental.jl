```
Peek(rows, maximum_length = 4)
```

名前付きタプルを返すイテレータをプレビューします。`maximum_length` 行を超えて表示されることはありません。

```jldoctest Peek
julia> using LightQuery


julia> Peek(Rows(a = 1:5, b = 5:-1:1))
Showing 4 of 5 rows
|   a |   b |
| ---:| ---:|
|   1 |   5 |
|   2 |   4 |
|   3 |   3 |
|   4 |   2 |
```
