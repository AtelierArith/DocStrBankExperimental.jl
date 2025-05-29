```
find_first(A [,a...]; dict=false)
```

The first index of selected Array element

A: string/array of elements of the same type

default  : Array containing the first index (indices) of selected elements of A (default: all elements)

dict=true: Dict for the first index (indices) of selected elements of A (default: all elements)

#### Examples:

```
A = [:📑,:📌,:📢,:📌,:📞]
B = [1,2,3,2,5]
str = "aβcβd";

find_first(A) == find_first(B) == find_first(str)
true

find_first(A,:📌)
1-element Array{Array{Int64,1},1}:
 2

find_last(A,:📌; dict=true)
1-element Array{Pair{Symbol,Int64},1}:
 :📌 => 2

find_last(A; dict=true)
4-element Array{Pair{Symbol,Int64},1}:
 :📑 => 1
 :📌 => 2
 :📢 => 3
 :📞 => 5

find_first(str)
4-element Array{Int64,1}:
 1
 2
 3
 5
```
