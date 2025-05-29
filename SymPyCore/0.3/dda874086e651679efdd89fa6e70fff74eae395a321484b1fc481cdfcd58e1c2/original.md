```
lambdify(ex, vars...;
         fns=Dict(), values=Dict,
         expression = Val{false},
         conv = walk_expression,
         use_julia_code=false,
         invoke_latest=true)
```

Take a symbolic expression and return a `Julia` struct subtyping `Function` or expression to build a function. The struct contains the expression.

  * `ex::Sym` a symbolic expression with 0, 1, or more free symbols
  * `vars` Either a tuple of variables or each listed separately, defaulting to `free_symbols(ex)` and its ordering. If `vars` is empty, a 0-argument function is returned.
  * `fns::Dict`, `vals::Dict`: Dictionaries that allow customization of the function that walks the expression `ex` and creates the corresponding AST for a Julia expression. See `SymPy.fn_map` and `SymPy.val_map` for the default mappings of sympy functions and values into `Julia`'s AST.

# `expression`: the default, `Val{false}`, will return a callable struct; passing `Val{true}` will return the expression. (This is also in the `expr` field of the struct, so changing this is unnecessary.) (See also `invoke_latest=false`.)

  * `conv`: a method to convert a symbolic expression into an expression. The default is part of this package; the alternative, the unexpored `julia_code`, is from the Python package. (See also `use_julia_code`)
  * `use_julia_code::Bool`: use SymPy's conversion to an expression, the default is `false`
  * `invoke_latest=true`: if `true` will call `eval` and `Base.invokelatest` to return a function that should not have any world age issue. If `false` will return a Julia expression that can be `eval`ed to produce a function.

Example:

```jldoctest lambdify
julia> using SymPyPythonCall

julia> @syms x y z
(x, y, z)

julia> ex = x^2 * sin(x)
 2
x ⋅sin(x)

julia> fn = lambdify(ex);

julia> fn(pi)
0.0

julia> ex = x + 2y + 3z
x + 2⋅y + 3⋅z

julia> fn = lambdify(ex);

julia> fn(1,2,3) # order is by free_symbols
14

julia> ex(x=>1, y=>2, z=>3)
14

julia> fn = lambdify(ex, (y,x,z));

julia> fn(1,2,3)
13
```

!!! note
    The default produces slower functions due to the calls to `eval` and `Base.invokelatest`.  In the following `g2` (which, as seen, requires additional work to compute) is as fast as calling `f` (on non symbolic types), whereas `g1` is an order of magnitude slower in this example.


```julia lambdify
julia> @syms x
(x,)

julia> f(x) = exp(cot(x))
f (generic function with 1 method)

julia> g1 = lambdify(f(x));

julia> ex = lambdify(f(x), invoke_latest=false);

julia> @eval g2(x) = ($ex)(x)
g2 (generic function with 1 method)
```

A performant and easy alternative, say, is to use `GeneralizedGenerated`'s `mk_function`, as follows:

```julia
julia> using GeneralizedGenerated, BenchmarkTools

julia> f(x,p) = x*tanh(exp(p*x));

julia> @syms x p; g = lambdify(f(x,p), x, p)
Callable function with variables (:x, :p)

julia> gg = mk_function(g...);

julia> @btime $g(1,2)
  48.862 ns (1 allocation: 16 bytes)
0.9999992362042291

julia> @btime $gg(1,2)
 1.391 ns (0 allocations: 0 bytes)
0.9999992362042291

julia> @btime $f(1,2)
  1.355 ns (0 allocations: 0 bytes)
0.9999992362042291

```

As seen, the function produced by `GeneralizedGenerated` is as performant as the original, and **much** more so than calling that returned by `lambdify`, which uses a call to `Base.invokelatest`.
