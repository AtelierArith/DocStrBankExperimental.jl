```
find_all(A [,a...]; count=false)
```

A: 同じ型の要素の文字列/配列

デフォルト   : Aの選択された要素のインデックス（インデックス）の配列（デフォルト：すべての要素）

count=true: Aの選択された要素に対して見つかったインデックスの数（デフォルト：すべての要素）

#### 例:

```
A = [:📑,:📌,:📢,:📌,:📞]
B = [1,2,3,2,5]
str = "aβcβd";
find_all(A) == find_all(B) == find_all(str)
true

find_all(A,:📌)
1-element Array{Array{Int64,1},1}:
 [2, 4]

find_all(str)
4-element Array{Array{Int64,1},1}:
 [1]
 [2, 4]
 [3]
 [5]

find_all(A; count=true)
4-element Array{Int64,1}:
 1
 2
 1
 1

str = "📑📌📢📌📞"
find_all(str,'📌')
1-element Array{Array{Int64,1},1}:
 [2, 4]
```
