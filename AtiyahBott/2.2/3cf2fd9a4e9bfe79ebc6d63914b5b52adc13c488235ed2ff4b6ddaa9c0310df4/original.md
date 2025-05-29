```
AtiyahBottFormula(n, d, m, P; do_check, show_bar)
```

Apply the Atiyah-Bott residue formula to the class `P`, in the moduli space of rational marked stable maps to the projective space of dimension `n` of degree `d` with `m` marks.

# Arguments

  * `n::Int64`: the dimension of the projective space.
  * `d::Int64`: the degree of the stable maps, it must be positive.
  * `m::Int64`: the number of marks.
  * `P`: the equivariant class.
  * `do_check::Bool`: if `true`, checks if `P` is a well defined zero cycle, and stops the computation if this is not true. If `false`, the computation may have an unexpected behaviour. By default is `true`.
  * `show_bar::Bool`: hide the progress bar if and only if this condition is `false`. By default is `true`.

The general construction of `P` is the following:

```julia-repl
julia> P = 
```

After `=`, one has to write an expression in the equivariant classes. The expression is a combination of the equivariant classes. We compute the degree of `P` by

```julia-repl
julia> AtiyahBottFormula(n, d, m, P);
```

# Example

```julia-repl
julia> P = Hypersurface(5);
julia> AtiyahBottFormula(3, 1, 0, P);
Warning: the class is not a 0-cycle.
julia> AtiyahBottFormula(4, 1, 0, P);
Result: 2875
julia> AtiyahBottFormula(4, 1, 0, P, do_check = false); #skip the preliminary check on `P`
julia> AtiyahBottFormula(4, 1, 0, P, show_bar = false); #it does not show the progress bar
```

The function returns an array of the same dimension of `P` (non-vectorized classes are assumed as 1-dimensional arrays). The Julia notation for accessing to array is `name_of_array[i]` where `i` is an index starting from 1.

# Example

```julia-repl
julia> P = Incidency(2)*Hypersurface(3);
julia> x = AtiyahBottFormula(3, 2, 0, P)[1];
Result: 81
julia> x
81
```

The class `P` supports parameters.

```julia-repl
julia> P = Hypersurface(3)*(Incidency(2)//3)^(d-1);
julia> d = 2;
julia> AtiyahBottFormula(3, d, 0, P);
Result: 27
julia> d = 3;
julia> AtiyahBottFormula(3, d, 0, P);
Result: 84
```

More examples are available in the support of the equivariant classes. It is enough to type `?` and then the name of the class. Currently, the supported classes are:

  * `O1_i(j)`         (Euler class of $\mathrm{ev}_j^*\mathcal{O}_{\mathbb{P}^n}(1)$)
  * `O1()`            (product of all `O1_i`)
  * `Psi(a)`          (cycle of $\psi$-classes)
  * `Jet(p,q)`        (Euler class of the jet bundle $J^p$ of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(q)$)
  * `Hypersurface(b)` (Euler class of the direct image of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(b)$)
  * `Incidency(r)`    (cycle parameterizing curves meeting a linear subspace of codimension $r$)
  * `Contact()`       (cycle parameterizing contact curves)
  * `R1(k)`           (first derived functor of direct image of $\mathrm{ev}^*\mathcal{O}_{\mathbb{P}^n}(-k)$)

To add more classes, please contact the authors.
