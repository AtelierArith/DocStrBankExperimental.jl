```
uniform_tree(n)
```

Generates a random labelled tree, drawn uniformly at random over the $n^{n-2}$ such trees. A uniform word of length `n-2` over the alphabet `1:n` is generated (Prüfer sequence) then decoded. See also the `prufer_decode` function and [this page on Prüfer codes](https://en.wikipedia.org/wiki/Pr%C3%BCfer_sequence). 

### Optional Arguments

  * `rng=nothing`: set the Random Number Generator.

# Examples

```jldoctest
julia> using Graphs

julia> uniform_tree(10)
{10, 9} undirected simple Int64 graph
```
