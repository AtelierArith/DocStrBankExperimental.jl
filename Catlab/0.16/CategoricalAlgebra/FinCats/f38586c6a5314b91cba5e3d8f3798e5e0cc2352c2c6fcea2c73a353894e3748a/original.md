Is the purported functor on a presented category functorial?

This function checks that functor preserves domains and codomains. When `check_equations` is `true` (the default is `false`), it also purports to check that the functor preserves all equations in the domain category. No nontrivial  checks are currently implemented, so this only functions for identity functors.

See also: [`functoriality_failures'](@ref) and [`is_natural`](@ref).
