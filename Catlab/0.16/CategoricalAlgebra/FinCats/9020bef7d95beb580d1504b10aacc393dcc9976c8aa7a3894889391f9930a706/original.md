Is the transformation between `FinDomFunctors` a natural transformation?

This function uses the fact that to check whether a transformation is natural, it suffices to check the naturality equations on a generating set of morphisms of the domain category. In some cases, checking the equations may be expensive or impossible. When the keyword argument `check_equations` is `false`, only the domains and codomains of the components are checked.

See also: [`is_functorial`](@ref).
