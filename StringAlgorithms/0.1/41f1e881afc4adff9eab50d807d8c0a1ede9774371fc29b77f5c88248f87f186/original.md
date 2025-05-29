```julia
z_algorithm(v)

```

Z Algorithm calculates the longest common prefix of each suffix of the given vector and the whole vector itself. Specially, the Z value of the whole vector is forced to be 0.

# Sample usages

> Usages of Z Algorithm are almost the same as the prefix function.


  * Finding all matches

```jldoctest
# The following function finds all occurrences of the pattern in the given vector, including overlapping ones.
function findall(pattern, s)
    n, m = length(s), length(pattern)
    tmp = vcat(collect(pattern), [nothing], collect(s))
    z = z_algorithm(tmp)
    return [i:i+m-1 for i in 1:n if z[i+m+1] == m]
end

findall("aba", "ddabababacc")

# output

3-element Vector{UnitRange{Int64}}:
 3:5
 5:7
 7:9
```
