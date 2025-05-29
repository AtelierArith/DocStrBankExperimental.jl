```
groebner_walk(
  I::MPolyIdeal, 
  target::MonomialOrdering = lex(base_ring(I)),
  start::MonomialOrdering = default_ordering(base_ring(I));
  perturbation_degree = ngens(base_ring(I)),
  algorithm::Symbol = :standard
)
```

Compute a reduced Groebner basis w.r.t. to a monomial ordering by converting it using the Groebner Walk.

# Arguments

  * `I::MPolyIdeal`: ideal one wants to compute a Groebner basis for.
  * `target::MonomialOrdering=:lex`: monomial ordering one wants to compute a Groebner basis for.
  * `start::MonomialOrdering=:degrevlex`: monomial ordering to begin the conversion.
  * `perturbationDegree::Int=2`: the perturbation degree for the perturbed Walk.
  * `algorithm::Symbol=:standard`: strategy of the Groebner Walk. One can choose between:

      * `standard`: Standard Walk [Cox.Little.OShea:2005](@cite),
      * `generic`: Generic Walk [Fukuda.Jensen.ea:2007](@cite),
      * `perturbed`: Perturbed Walk [Amrhein.Gloor.ea:1996](@cite).

# Examples

```jldoctest
julia> R,(x,y) = polynomial_ring(QQ, ["x","y"]);

julia> I = ideal([y^4+ x^3-x^2+x,x^4]);

julia> groebner_walk(I, lex(R))
Gröbner basis with elements
1 -> x + y^12 - y^8 + y^4 r
2 -> y^16
with respect to the ordering
lex([x, y])

julia> groebner_walk(I, lex(R); algorithm=:perturbed)
Gröbner basis with elements
1 -> x + y^12 - y^8 + y^4
2 -> y^16
with respect to the ordering
lex([x, y])

julia> set_verbosity_level(:groebner_walk, 1);
julia> groebner_walk(I, lex(R))
Results for standard_walk
Crossed Cones in: 
ZZRingElem[1, 1]
ZZRingElem[4, 3]
ZZRingElem[4, 1]
ZZRingElem[12, 1]
Cones crossed: 4
Gröbner basis with elements
1 -> x + y^12 - y^8 + y^4
2 -> y^16
with respect to the ordering
lex([x, y])

julia> groebner_walk(I, lex(R); algorithm=:perturbed)
perturbed_walk results
Crossed Cones in: 
[4, 3]
[4, 1]
[5, 1]
[12, 1]
[1, 0]
Cones crossed: 5
Gröbner basis with elements
1 -> y^16
2 -> x + y^12 - y^8 + y^4
with respect to the ordering
matrix_ordering([x, y], [1 0; 0 1])
```
