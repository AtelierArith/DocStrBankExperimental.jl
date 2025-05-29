```
nexprs(f, n::Int)
```

Create `n` similar expressions by evaluating `f`.

# Example

```jldoctest
julia> nexprs(5) do k
           :(1 + $k)
       end
quote
    1 + 1
    1 + 2
    1 + 3
    1 + 4
    1 + 5
end
```
