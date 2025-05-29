```
find_last(A [,a...]; dict=false)
```

The last index of selected Array element

A: string/array of elements of the same type

default  : Array containing the lasst index (indices) of selected elements of A (default: all elements)

dict=true: Dict for the lasst index (indices) of selected elements of A (default: all elements)

#### Examples:

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
