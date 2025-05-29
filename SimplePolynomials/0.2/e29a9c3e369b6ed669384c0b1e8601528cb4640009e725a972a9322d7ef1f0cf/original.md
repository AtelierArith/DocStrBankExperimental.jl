`make_function(p::SimplePolynomial)` or `make_function(f::SimpleRationalFunction)` returns a Julia `Function` that evaluates `p` or `f`. Of course one can use `p(x)` or `f(x)`, but the function returned can then be passed to (for example) `plot`.

Please note that `p(x)` [or `f(x)`] is already quite efficient.
