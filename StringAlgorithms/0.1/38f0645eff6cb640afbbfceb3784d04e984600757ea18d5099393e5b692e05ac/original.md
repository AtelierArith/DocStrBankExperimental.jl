```julia
prefix_function(v)

```

For each prefix of the given vector, calculate the maximum length such that its nontrivial prefix (not itself) equals to its suffix.

For example, for string `ababc`,

  * `p[1] = 0`
  * `p[2] = 0`
  * `p[3] = 1`, since the prefix `aba` has both prefix `a` and suffix `a`
  * `p[4] = 2`, since the prefix `abab` has both prefix `ab` and suffix `ab`
  * `p[5] = 0`

# Sample usages

  * Finding all matches (KMP algorithm)

```jldoctest
# The following function finds all occurrences of the pattern in the given vector, including overlapping ones.
function findall(pattern, s)
    n, m = length(s), length(pattern)
    tmp = vcat(collect(pattern), [nothing], collect(s))
    p = prefix_function(tmp)
    return [i-m+1:i for i in 1:n if p[i+m+1] == m]
end

findall("aba", "ddabababacc")

# output

3-element Vector{UnitRange{Int64}}:
 3:5
 5:7
 7:9
```
