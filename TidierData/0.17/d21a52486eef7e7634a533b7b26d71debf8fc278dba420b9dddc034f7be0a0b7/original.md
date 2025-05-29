```
@pull(df, column)
```

Pull (or extract) a column as a vector.

# Arguments

  * `df`: A DataFrame.
  * `column`: A single column, referred to either by its name or number.

# Examples

```jldoctest
julia> df = DataFrame(a = 'a':'e', b = 1:5, c = 11:15);
  
julia> @chain df @pull(a)
5-element Vector{Char}:
 'a': ASCII/Unicode U+0061 (category Ll: Letter, lowercase)
 'b': ASCII/Unicode U+0062 (category Ll: Letter, lowercase)
 'c': ASCII/Unicode U+0063 (category Ll: Letter, lowercase)
 'd': ASCII/Unicode U+0064 (category Ll: Letter, lowercase)
 'e': ASCII/Unicode U+0065 (category Ll: Letter, lowercase)

julia> @chain df @pull(2)
5-element Vector{Int64}:
 1
 2
 3
 4
 5
```
