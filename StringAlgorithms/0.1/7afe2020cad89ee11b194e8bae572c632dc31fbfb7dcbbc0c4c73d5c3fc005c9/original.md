```julia
manacher(v)

```

The Manacher algorithm proposed by Glenn K. Manacher in 1975.

Given a vector of length `n`, so that there will be `2n+1` positions if the intervals between each element are included, returns a vector of length `2n+1` denoting the longest palindrome centered at each position.

# Sample usages

  * Finding the length of the longest palindromic substring

```jldoctest
function longest_palindromic_substring(s)
    return maximum(manacher(s))
end

longest_palindromic_substring("ddabababacc")

# output

7
```
