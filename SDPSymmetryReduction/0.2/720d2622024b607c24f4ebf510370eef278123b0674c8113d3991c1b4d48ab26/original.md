```
dim(ap::AbstractPartition)
```

The dimension of the partition subspace `ap`.

# !!! note

# The `0`-set (the first subset) has a special meaning and is not accounted

# for the calculation.

# Examples

```julia
julia> q = SR.Partition(Float64[
           1 1 0;
           1 0 5;
           0 3 3
       ]);

julia> SR.dim(q)
3

julia> p = SR.Partition([
           1 1 2;
           1 2 5;
           2 3 3
       ]);

julia> SR.dim(p)
4

```
