```
@foreach_chain_candidate chain_var i_start i_end chain_length inner_expr
```

Iterate over all ascending tuples `(i_start, ..., i_end)` with length `chain_length`. This tuple will be named `chain_var` within the inner expression block.

# Example

```jldoctest
@foreach_chain_candidate I 1 5 4 begin
    @show I
end

# output

I = (1, 1, 1, 5)
I = (1, 1, 2, 5)
I = (1, 1, 3, 5)
I = (1, 1, 4, 5)
I = (1, 1, 5, 5)
I = (1, 2, 2, 5)
I = (1, 2, 3, 5)
I = (1, 2, 4, 5)
I = (1, 2, 5, 5)
I = (1, 3, 3, 5)
I = (1, 3, 4, 5)
I = (1, 3, 5, 5)
I = (1, 4, 4, 5)
I = (1, 4, 5, 5)
I = (1, 5, 5, 5)
```
