## `sweepcut`

A sweepcut is an operation that takes an order to the vertices of a graph and evaluates the cut and volume of every partition induced by a prefix of that ordering. That is, if the order of vertices is

```
v1, v2, v3, ...
```

the the sweep cut evaluates

```
cut({v1}), vol({v1})
cut({v1,v2}), vol({v1,v2})
cut({v1,v2,v3}), vol({v1,v2,v3})
...
```

where cut is the total edge weight that connects vertices in S to the graph. And vol is the total edge weight connecting

## Functions

  * `profile = sweepcut(A,x::Vector{T})` A standard sweepcut call that will get a sweepcut for a vector where x is sorted to get the order of the vertices (decreasing order). This is useful if you have a vector that should indicate good cuts in the graph, such as the Fiedler vector.
  * `profile = sweepcut(A,p,r,totalvol,maxvol)` the in-depth call that all others are converted into. We strongly recommend against calling this yourself unless you understand the sweepcut code.

## Inputs

  * `A`: the sparse matrix representing the symmetric graph
  * `x`: A vector scoring each vertex. This will be sorted and      turned into one of the other inputs.
  * `p`: a partial permutation vector over the vertices of the graph       This vector needs to list every vertex at most once.       It could be shorter and need not list every vertex.
  * `r`: A general data structure that gives       the rank of an item in the permutation vector       p should be sorted in decreasing order so that       i < j means that r[p[i]] < r[p[j]]
  * `totalvol`: the total volume of the graph
  * `maxvol`: the maximum volume of any set considered

## Returns

A `SweepcutProfile` type with all the information computed in the sweepcut. Most likely, you want the result `bestset` as indicated below.

## Example

```
A = load_matrix_network("minnesota")
v = fiedler_vector(A)[1] # get the
p = sweepcut(A,v)
S = bestset(p) # get the bestset from the profile
T = spectral_cut(A).set # should give you the same set
# using UnicodePlots; lineplot(p.conductance) # show the conductance
```
