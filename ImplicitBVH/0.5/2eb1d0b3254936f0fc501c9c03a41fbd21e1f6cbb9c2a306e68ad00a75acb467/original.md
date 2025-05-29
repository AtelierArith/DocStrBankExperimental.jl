```julia
struct BVHTraversal{C1<:(AbstractVector), C2<:(AbstractVector)}
```

Collected BVH traversal `contacts` vector, some stats, plus the two buffers `cache1` and `cache2` which can be reused for future traversals to minimise memory allocations.

# Fields

  * `start_level1::Int`: the level at which the single/pair-tree traversal started for the first BVH.
  * `start_level2::Int`: the level at which the pair-tree traversal started for the second BVH.
  * `num_checks::Int`: the total number of contact checks done.
  * `num_contacts::Int`: the number of contacts found.
  * `contacts::view(cache1, 1:num_contacts)`: the contacting pairs found, as a view into `cache1`.
  * `cache1::C1{IndexPair} <: AbstractVector`: first BVH traversal buffer.
  * `cache2::C2{IndexPair} <: AbstractVector`: second BVH traversal buffer.
