```
@rule LHS => RHS
```

Creates a `Rule` object. A rule object is callable, and takes an expression and rewrites it if it matches the LHS pattern to the RHS expression, returns `nothing` otherwise. The rule language is described below.

LHS can be any possibly nested function call expression where any of the arguments can optionally be a Slot (`~x`) or a Segment (`~x...`) (described below).

If an expression matches LHS entirely, then it is rewritten to the result of the expression RHS, whose local scope includes the slot matches as variables.

**Slot**:

A Slot variable is written as `~x` and matches a single expression. `x` is the name of the variable. If a slot appears more than once in an LHS expression then expression matched at every such location must be equal (as shown by `isequal`).

*Example:*

Simple rule to turn any `sin` into `cos`:

```julia
julia> @syms a b c
(a, b, c)

julia> r = @rule sin(~x) => cos(x)
sin(~x) => cos(x)

julia> r(sin(1+a))
cos((1 + a))
```

A rule with 2 segment variables

```julia
julia> r = @rule sin(~x + ~y) => sin(x)*cos(y) + cos(x)*sin(y)
sin(~x + ~y) => sin(x) * cos(y) + cos(x) * sin(y)

julia> r(sin(a + b))
cos(a)*sin(b) + sin(a)*cos(b)
```

A rule that matches two of the same expressions:

```julia
julia> r = @rule sin(~x)^2 + cos(~x)^2 => 1
sin(~x) ^ 2 + cos(~x) ^ 2 => 1

julia> r(sin(2a)^2 + cos(2a)^2)
1

julia> r(sin(2a)^2 + cos(a)^2)
# nothing
```

**Segment**:

A Segment variable matches zero or more expressions in the function call. Segments may be written by splatting slot variables (`~x...`).

*Example:*

This implements the distributive property of multiplication: `+(~ys...)` matches expressions like `a + b`, `a+b+c` and so on. On the RHS `ys` presents as any old julia array.

```julia
julia> r = @rule ~x * +((~ys...)) => sum(map(y-> x * y, ys));

julia> r(2 * (a+b+c))
((2 * a) + (2 * b) + (2 * c))
```

**Predicates**:

There are two kinds of predicates, namely over slot variables and over the whole rule. For the former, predicates can be used on both `~x` and `~x...` like `~x::f` or `~x::f...`. Here `f` can be any julia function. In the case of a slot the function gets a single matched subexpression, in the case of segment, it gets an array of matched expressions.

The predicate should return `true` if the current match is acceptable, and `false` otherwise.

```julia
julia> two_πs(x::Number) = abs(round(x/(2π)) - x/(2π)) < 10^-9
two_πs (generic function with 1 method)

julia> two_πs(x) = false
two_πs (generic function with 2 methods)

julia> r = @rule sin(+(~x..., ~y::two_πs, ~z...)) => sin(+(x..., z...))
sin(+(x..., y::two_πs, z...)) => sin(+(x..., z...))

julia> r(sin(a+3π))

julia> r(sin(a+6π))
sin(a)

julia> r(sin(a+6π+c))
sin((a + c))
```

For the predicate over the whole rule, use `@rule <LHS> => <RHS> where <predicate>`:

```
julia> @syms a b;

julia> predicate(x) = x === a;

julia> r = @rule ~x => x where f(x);

julia> r(a)
a

julia> r(b) === nothing
true
```

Note that this is syntactic sugar and that it is the same as something like `@rule ~x => f(x) ? x : nothing`.

**Compatibility**: Segment variables may still be written as (`~~x`), and slot (`~x`) and segment (`~x...` or `~~x`) syntaxes on the RHS will still substitute the result of the matches.

See also: [`@capture`](@ref)
