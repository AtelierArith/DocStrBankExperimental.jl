```
inc1(n, _) -> n + 1
```

A reducing function for counting elements.  It increments the first argument by one.

# Examples

```jldoctest
julia> using DataTools
       using Transducers

julia> inc1(10, :ignored)
11

julia> inc1(Init(inc1), :ignored)
1

julia> foldl(inc1, Map(identity), 'a':2:'e')
3

julia> foldl(TeeRF(+, inc1), Map(identity), 1:2:10)  # sum and count
(25, 5)

julia> rf = oncol(:a => (+) => :sum, :a => inc1 => :count);

julia> foldl(rf, Map(identity), [(a = 1, b = 2), (a = 2, b = 3)])
(sum = 3, count = 2)
```
