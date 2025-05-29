```
find_last(A [,a...]; dict=false)
```

選択された配列要素の最後のインデックス

A: 同じ型の要素の文字列/配列

デフォルト  : 選択された要素の最後のインデックス（インデックス）の配列（デフォルト: すべての要素）

dict=true: 選択された要素の最後のインデックス（インデックス）の辞書（デフォルト: すべての要素）

#### 例:

```
A = [:📑,:📌,:📢,:📌,:📞]
B = [1,2,3,2,5]
str = "aβcβd";
find_last(A) == find_first(B) == find_first(str)
true

find_last(A,:📌)
1-element Array{Array{Int64,1},1}:
 4

find_last(A,:📌; dict=true)
1-element Array{Pair{Symbol,Int64},1}:
 :📌 => 4

find_last(A; dict=true)
4-element Array{Pair{Symbol,Int64},1}:
 :📑 => 1
 :📌 => 4
 :📢 => 3
 :📞 => 5

find_last(str)
4-element Array{Int64,1}:
 1
 4
 3
 5
```
