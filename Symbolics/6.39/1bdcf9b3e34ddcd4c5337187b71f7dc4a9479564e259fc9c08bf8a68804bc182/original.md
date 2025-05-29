```
symbolic_solve(expr, x; dropmultiplicity=true, warns=true)
```

`symbolic_solve` is a function which attempts to solve input equations/expressions symbolically using various methods.

## Arguments

  * expr: Could be a single univar expression in the form of a poly or multiple univar expressions or multiple multivar polys or a transcendental nonlinear function.
  * x: Could be a single variable or an array of variables which should be solved
  * dropmultiplicity (optional): Should the output be printed `n` times where `n` is the number of occurrence of the root? Say we have `(x+1)^2`, we then have 2 roots `x = -1`, by default the output is `[-1]`, If dropmultiplicity is inputted as false, then the output is `[-1, -1]`.
  * warns (optional): When invalid expressions or cases are inputted, should the solver warn you of such cases before returning nothing? if this is set to false, the solver returns nothing. By default, warns are set to true.

## Supported input

The base solver (`symbolic_solve`) has multiple solvers which chooses from depending on the the type of input (multiple/uni var and multiple/single expression) only after ensuring that the input is valid.

The expressions inputted can contain parameters, which are assumed to be transcendental. A parameter "a" is transcendental if there exists no polynomial P with rational coefficients such that P(a) = 0. Check the examples section.

Currently, `symbolic_solve` supports

  * Linear and polynomial equations (with parameters)
  * Systems of linear and polynomials equations (without extra parameters, for now)
  * Equations with transcendental functions (with parameters)

## Examples

### `solve_univar` (uses factoring and analytic solutions up to degree 4)

!!! note
    The package `Nemo` is needed in order to use `solve_univar` as well as `solve_multipoly`, so executing `using Nemo` as you will see in the following examples is necessary; otherwise, the function will throw an error.


```jldoctest
julia> using Symbolics, Nemo;

julia> @variables x a b;

julia> expr = expand((x + b)*(x^2 + 2x + 1)*(x^2 - a))
-a*b - a*x - 2a*b*x - 2a*(x^2) + b*(x^2) + x^3 - a*b*(x^2) - a*(x^3) + 2b*(x^3) + 2(x^4) + b*(x^4) + x^5

julia> symbolic_solve(expr, x)
4-element Vector{Any}:
 -1
   -b
   (1//2)*√(4a)
   (-1//2)*√(4a)

julia> symbolic_solve(expr, x, dropmultiplicity=false)
5-element Vector{Any}:
 -1
 -1
   -b
   (1//2)*√(4a)
   (-1//2)*√(4a)
```

```jldoctest
julia> symbolic_solve(x^2 + a*x + 6, x)
2-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (1//2)*(-a + √(-24 + a^2))
 (1//2)*(-a - √(-24 + a^2))
```

```jldoctest
julia> symbolic_solve(x^7 - 1, x)
2-element Vector{Any}:
  roots_of((1//1) + x + x^2 + x^3 + x^4 + x^5 + x^6, x)
 1
```

### `solve_multivar` (uses Groebner basis and `solve_univar` to find roots)

!!! note
    Similar to `solve_univar`, `Groebner` is needed for `solve_multivar` or to be fully functional.


```jldoctest
julia> using Groebner

julia> @variables x y z
3-element Vector{Num}:
 x
 y
 z

julia> eqs = [x+y^2+z, z*x*y, z+3x+y]
3-element Vector{Num}:
 x + z + y^2
       x*y*z
  3x + y + z

julia> symbolic_solve(eqs, [x,y,z])
3-element Vector{Any}:
 Dict{Num, Any}(z => 0, y => 1//3, x => -1//9)
 Dict{Num, Any}(z => 0, y => 0, x => 0)
 Dict{Num, Any}(z => -1, y => 1, x => 0)
```

!!! note
    If `Nemo` or `Groebner` are not imported when needed, the solver throws an error.


```jldoctest
julia> using Symbolics

julia> @variables x y z;

julia> symbolic_solve(x+1, x)
ERROR: "Nemo is required. Execute `using Nemo` to enable this functionality."

julia> symbolic_solve([x+1, y], [x, y])
ERROR: "Groebner bases engine is required. Execute `using Groebner` to enable this functionality."
```

### `solve_multipoly` (uses GCD between the input polys)

```jldoctest
julia> symbolic_solve([x-1, x^3 - 1, x^2 - 1, (x-1)^20], x)
1-element Vector{BigInt}:
 1
```

### `ia_solve` (solving by isolation and attraction)

```jldoctest
julia> symbolic_solve(2^(x+1) + 5^(x+3), x)
1-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (-slog(2) - log(complex(-1)) + 3slog(5)) / (slog(2) - slog(5))
```

```jldoctest
julia> symbolic_solve(log(x+1)+log(x-1), x)
2-element Vector{SymbolicUtils.BasicSymbolic{BigFloat}}:
 (1//2)*√(8.0)
 (-1//2)*√(8.0)
```

```jldoctest
julia> symbolic_solve(a*x^b + c, x)
((-c)^(1 / b)) / (a^(1 / b))
```

### Evaluating output (converting to floats)

If you want to evaluate the exact expressions found by `symbolic_solve`, you can do the following:

```jldoctest
julia> roots = symbolic_solve(2^(x+1) + 5^(x+3), x)
1-element Vector{SymbolicUtils.BasicSymbolic{Real}}:
 (-slog(2) - log(complex(-1)) + 3slog(5)) / (slog(2) - slog(5))

julia> Symbolics.symbolic_to_float.(roots)
1-element Vector{Complex{BigFloat}}:
 -4.512941594732059759689023145584186058252768936052415430071569066192919491762214 + 3.428598090438030380369414618548038962770087500755160535832807433942464545729382im
```
