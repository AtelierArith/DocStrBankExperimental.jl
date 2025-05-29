```
getindex!(cache,a::AbstractArray,i...)
```

Returns the item of the array `a` associated with index `i` by (possibly) using the scratch data passed in the `cache` object.

It defaults to

```
getindex!(cache,a::AbstractArray,i...) = a[i...]
```

As for standard Julia arrays, the user needs to implement only one of the following signatures depending on the `IndexStyle` of the array.

```
getindex!(cache,a::AbstractArray,i::Integer)
getindex!(cache,a::AbstractArray{T,N},i::Vararg{Integer,N}) where {T,N}
```

# Examples

Iterating over an array using the `getindex!` function

```jldoctest
using Gridap.Arrays

a = collect(10:15)

cache = array_cache(a)
for i in eachindex(a)
  ai = getindex!(cache,a,i)
  println("$i -> $ai")
end

# output
1 -> 10
2 -> 11
3 -> 12
4 -> 13
5 -> 14
6 -> 15
```
