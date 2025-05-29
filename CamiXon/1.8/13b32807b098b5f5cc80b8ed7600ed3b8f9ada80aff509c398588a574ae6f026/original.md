```
autoNtot(n::Int)
```

Total number of gridpoints (rule of thumb value)

$$
    N_{tot} = 400 + 100\ n,
$$

where $n$ is the principal quantum number

### Example:

```
julia> autoNtot(1)
500
```
