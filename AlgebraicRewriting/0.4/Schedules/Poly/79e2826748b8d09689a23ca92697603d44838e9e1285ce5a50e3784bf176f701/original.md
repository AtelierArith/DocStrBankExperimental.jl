Quotes in this docstring and others taken from David Spivak: https://topos.site/blog/2023/09/powers-of-polynomial-monads/#exponentiating-monads

"A polynomial monad is a polynomial functor t with coherent maps η: y → t and  μ: t ◁ t → t.

Polynomial monads can be thought of as offering compositional (possibly labeled)  packages with some number of slots. The compositionality of this packaging says  that (via the monad unit) we know how to package up a given element of any set,  and that (via the monad multiplication) we can take a package of packages and  simplify it to a single package."

We consider monads t of the form: t = Σ_{i ∈ t(1)} y^{t[i]}

I is the type of labels, e.g. probability weights.
