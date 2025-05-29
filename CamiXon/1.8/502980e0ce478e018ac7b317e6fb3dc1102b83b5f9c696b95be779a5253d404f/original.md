```
find_all(A [,a...]; count=false)
```

A: string/array of elements of the same type

default   : Array containing the index (indices) of selected elements of A (default: all elements)

count=true: The number of indices found for selected elements of A (default: all elements)

#### Examples:

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
