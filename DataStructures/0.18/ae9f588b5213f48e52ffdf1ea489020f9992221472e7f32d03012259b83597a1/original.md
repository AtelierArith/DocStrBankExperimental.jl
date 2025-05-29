```
Stack{T}([blksize::Integer=1024])
```

Create a `Stack` object containing elements of type `T` for Last In First Out (LIFO) access.

# Examples

```jldoctest
julia> s = Stack{Int}() # create a stack
Stack{Int64}(Deque [Int64[]])

julia> push!(s, 1) # push back a item
Stack{Int64}(Deque [[1]])

julia> x = top(s) # get a first item
1

julia> length(s)
1

julia> x = pop!(s) # get and remove a first item
1

julia> length(s)
0
```
