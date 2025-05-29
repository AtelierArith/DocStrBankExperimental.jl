```
@ga <sig> <T> <ex>
@ga <sig> <ex>
```

Generate Julia code which implements the computation of geometric elements from `ex` in an algebra defined by a signature `sig` (see [`SymbolicGA.Signature`](@ref)).

Supported syntax:

  * `sig`: Integer literal or tuple of 1, 2 or 3 integer literals corresponding to the number of positive, negative and degenerate basis vectors respectively, where unspecified integers default to zero. May also be a string literal of the form `<+++--𝟎>` where the number of `+`, `-` and `𝟎` correspond to the nmuber of positive, negative and degenerate basis vectors respectively.
  * `T`: Any arbitrary expression which evaluates to a type or to `nothing`.
  * `ex`: Any arbitrary expression that can be parsed algebraically.

See also: [`codegen_expression`](@ref).

`ex` can be a single statement or a block, and uses a domain-specific language to facilitate the construction of algebraic expressions. `ex` is logically divided into two sections: a definition section, which defines bindings, and a final algebraic expression, which will be the object of the evaluation. It is processed in three phases:

  * A definition phase, in which bindings are defined with one or several statements for use in the subsequent phase;
  * An expansion phase, where identified bindings in the final algebraic expression are expanded. The defined bindings include the ones priorly defined and a set of default bindings.
  * An evaluation phase, in which the core algebraic expression is simplified and translated into a Julia expression.

# Expression parsing

## Binding definitions

All statements prior to the last can define new variables or functions with the following syntax and semantics:

  * Variables are either declared with `<lhs::Symbol> = <rhs::Any>` or with `<lhs::Symbol>::<type>`, the latter being expanded to `<lhs> = <lhs>::<type>`.
  * Functions are declared with a standard short or long form function definition `<name>(<args...>) = <rhs>` or `function <name>(<args...>) <rhs> end`, and are restricted to simple forms to encode simple semantics. The restrictions are as follows:

      * `where` clauses and output type annotations are not supported.
      * Function arguments must be untyped, e.g. `f(x, y)` is allowed but not `f(x::Vector, y::Vector)`.
      * Function arguments must not be reassigned; it is assumed that any occurence of symbols declared as arguments will reference these arguments. For example, `f(x, y) = x + y` assumes that `x + y` actually means "perform `+` on the first and second function argument". Therefore, `f(x, y) = (x = 2; x) + y` will be likely to cause bugs. To alleviate this restriction, use [`codegen_expression`](@ref) with a suitable [`SymbolicGA.Bindings`] with function entries that contain specific calls to `:($(@arg <i>)).

## Binding expansion

References and functions are expanded in a fairly straightforward copy-paste manner, where references are replaced with their right-hand side and function calls with their bodies with their arguments interpolated. Simple checks are put in place to allow for self-referencing bindings for references, such as `x = x::T`, leading to a single expansion of such a pattern in the corresponding expression subtree.

See [`SymbolicGA.Bindings`](@ref) for more information regarding the expansion of such variables and functions.

Function calls will be assumed to be either referencing a binding or a built-in function. If you want to call a function, e.g. `my_func(x)::Vector`, you will have to interpolate the call: `$(my_func(x))::Vector`.

# Algebraic evaluation

Type annotations may either:

  * Specify what type of geometric entity an input should be considered as, where components are then picked off with `getcomponent`.
  * Request the projection of an intermediate expression over one or multiple grades.
