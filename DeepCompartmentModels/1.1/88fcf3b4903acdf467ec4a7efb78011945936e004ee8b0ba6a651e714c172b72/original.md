```
Combine([out_dim], pairs...)
```

Connects specific branches to specific outputs in a Lux model containing a BranchLayer.  Output from branches pointing to the same output are combined using a product.

# Arguments:

  * `pairs...`: Pairs denoting what branch to connected to what output(s). Pairs take the following format: i => [j] or [j, k, ...]

# Examples

```jldoctest
julia> layer = Combine(1 => [1], 2 => [1], 3 => [2]) # Connects branch 1 to output 1, branch 2 to output 1, etc.
Combine()
```
