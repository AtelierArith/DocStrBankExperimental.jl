```
Permutation
PermutationGroup
```

Give access to the `sympy.combinatorics.permutations` module

## Example

```jldoctest permutation
julia> using SymPyPythonCall

julia> p = Permutation([1,2,3,0])
(0 1 2 3)

julia> p^2
(0 2)(1 3)

julia> p^2 * p^2
()
```

Rubik's cube example from SymPy documentation

```jldoctest permutation
julia> F = Permutation([(2, 19, 21, 8),(3, 17, 20, 10),(4, 6, 7, 5)])
(2 19 21 8)(3 17 20 10)(4 6 7 5)

julia> R = Permutation([(1, 5, 21, 14),(3, 7, 23, 12),(8, 10, 11, 9)])
(1 5 21 14)(3 7 23 12)(8 10 11 9)

julia> D = Permutation([(6, 18, 14, 10),(7, 19, 15, 11),(20, 22, 23, 21)])
(6 18 14 10)(7 19 15 11)(20 22 23 21)

julia> G = PermutationGroup(F,R,D);

julia> G.order()
3674160
```
