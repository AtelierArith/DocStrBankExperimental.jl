Implicit equations defined by a context.

This function allows a generalized algebraic theory (GAT) to be expressed as an essentially algebraic theory, i.e., as partial functions whose domains are defined by equations.

References:

  * (Cartmell, 1986, Sec 6: "Essentially algebraic theories and categories with  finite limits")
  * (Freyd, 1972, "Aspects of topoi")

This function gives expressions for computing the elements of `c.context`   which can be inferred from applying accessor functions to elements of `args`.

Example:

> equations({f::Hom(a,b), g::Hom(b,c)}, {a::Ob, b::Ob, c::Ob}, ThCategory)


ways*of*computing = Dict(a => [dom(f)], b => [codom(f), dom(g)], c => [codom(g)],                          f => [f], g => [g])
