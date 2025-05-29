```
enumerate_definite_genus(known::Vector{ZZLat}, algorithm::Symbol = :default) -> Vector{ZZLat}, QQFieldElem
enumerate_definite_genus(L::ZZLat, algorithm::Symbol = :default) -> Vector{ZZLat}
enumerate_definite_genus(G::ZZGenus, algorithm::Symbol = :default) -> Vector{ZZLat}
```

Enumerate lattices in a given genus of integral definite lattices of rank at least `3`, using Kneser's neighbour algorithm.

The output consists of a list of lattices representing the isometry classes in the given genus.

For the first argument, one can choose to give directly a genus symbol $G$ or a lattice $L$ in $G$. Otherwise, one can give a list of known lattices $G$ to continue an incomplete enumeration (in which case the lattices are assumed to be in the same spinor genus).

The second argument gives the choice to which algorithm to use for the enumeration. We currently support two algorithms:

  * `:random` which finds new isometry classes by constructing neighbours from random isotropic lines;
  * `:orbit` which computes orbits of isotropic lines before constructing neighbours.

If `algorithm = :default`, the function chooses the most appropriate algorithm depending on the rank and determinant of the genus to be enumerated.

There are possible extra optional arguments:

  * `rand_neigh::Int` (default = `10`) -> for random enumeration, how many random neighbours are computed at each iteration;
  * `invariant_function::Function` (default = `default_invariant_function`) -> a function to compute isometry invariants in order to avoid unnecessary isometry tests;
  * `save_partial::Bool` (default = `false`) -> whether one wants to save iteratively new isometry classes (for instance for large genera);
  * `save_path::String` (default = `nothing`) -> a path to a folder where to save new lattices in the case where `save_partial` is true;
  * `use_mass::Bool` (default = `true`) -> whether to use the mass formula as termination condition;
  * `stop_after::IntExt` (default = `inf`) -> the algorithm stops after the specified amount of vain iterations without finding a new isometry class is reached;
  * `max::IntExt` (default = `inf`) -> the algorithm stops after finding `max` new isometry classes.

In the case where one gives a list of `known` lattices in input, the output list contains a copy of `known` together with any new lattice computed. The extra output of the function is a rational number giving the portion of the mass of the (spinor) genus which is missing. It is set to be `0` whenever the mass is not used (`use_mass = false`). Moreover, there are two other possible extra optional arguments:

  * `distinct::Bool` (default = `false`) -> whether the lattices in `known` are known to be pairwise non-isometric;
  * `missing_mass::QQFieldElem` (default = `nothing`) -> if `use_mass` and `distinct` are true, and the partial mass of `known` is known, gives what is the part of the mass which is missing;

If `distinct == false`, the function first compares all the lattices in `known` to only keep one representative for each isometry class represented.

If `save_partial == true`, the lattices are stored in a compact way in a `.txt` file. The storing only remembers the rank of a lattice, half of its Gram matrix (which is enough to reconstruct the lattice as a standalone object) and the order of the isometry group of the lattice if it has been computed.

The `default_invariant_function` currently computes:

  * the absolute length of a shortest vector in the given lattice (also known as [`minimum`](@ref));
  * an ordered list of tuples consisting of the decomposition of the root sublattice of the given lattice (see [`root_lattice_recognition`](@ref));
  * the kissing number of the given lattice, which is proportional to the number of vectors of shortest length;
  * the order of the isometry group of the given lattice.
