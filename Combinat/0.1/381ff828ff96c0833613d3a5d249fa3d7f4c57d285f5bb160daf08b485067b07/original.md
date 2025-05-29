This  module  started  as  a  Julia  port of combinatorics and basic number theory  functions  from  GAP.  See  comments  below  on  how it compares to `Combinatorics.jl`. The only dependency is the `Primes` package.

The list of functions it exports are:

Classical enumerations:

[`combinations`](@ref), [`arrangements`](@ref), [`permutations`](@ref), [`partitions`](@ref), [`partition_tuples`](@ref), [`compositions`](@ref), [`multisets`](@ref)

functions to count enumerations without computing them:

`ncombinations`, `narrangements`, `npartitions`, `npartition_tuples`, `ncompositions`, `nmultisets`

some functions on partitions and permutations:

[`lcm_partitions`](@ref), [`gcd_partitions`](@ref), [`conjugate_partition`](@ref), [`dominates`](@ref), [`tableaux`](@ref), [`robinson_schensted`](@ref)

counting functions:

[`bell`](@ref), [`stirling1`](@ref), [`stirling2`](@ref), [`catalan`](@ref), [`bernoulli`](@ref)

number theory

[`prime_residues`](@ref), [`primitiveroot`](@ref), [`moebius`](@ref)

some structural manipulations not (yet?) in Julia:

[`groupby`](@ref), [`tally`](@ref), [`tally_sorted`](@ref), [`collectby`](@ref), [`unique_sorted!`](@ref), [`union_sorted`](@ref), [`intersect_sorted`](@ref)

matrix blocks:

[`blocks`](@ref), [`diagblocks`](@ref)

Have  a  look  at  the  individual  docstrings  and  enjoy (any feedback is welcome).  

After  writing  most  of  this  module,  I  became  aware  of  the  package `Combinatorics`  which has a  considerable overlap. However  there are some discrepancies  between these  two packages  which make  `Combinatorics` not easily usable for me:

  * I often  use sorting  in algorithms  where `Combinatorics` uses hashing. So  the algorithms do  not always apply  to the same  types (sorting is often faster). For some algorithms, a keyword lets you choose a hashing variant.  Here hashable refers to a type  which has a `hash` method and sortable to a type which has an `isless` method.
  * `Combinatorics.combinations` does not include the empty subset.
  * I use lower  case for functions  that return enumerations  as a list and camel  case  for  iterators.  Many  enumerations  have  both  variants. `Combinatorics` has only one variant for enumerations, which is often a lowercase iterator.
  * `Combinatorics` has fewer enumerations.

A  less  fundamental  discrepancy  concerns  names. However I would welcome discussions  with the authors of `Combinatorics` to see if the two packages could be made more compatible in this respect.
