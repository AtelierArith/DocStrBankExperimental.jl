```
@_ func(ex1, [ex2 ...])
```

Convert `ex1,ex2,...` into anonymous functions when they have `_` placeholders, and *pass them along* to `func`.

The detailed rules are:

1. Uses of the placeholder `_` expand to the single argument of an anonymous function which is passed to the outermost ordinary function call.
2. Numbered placeholders `_1,_2,...` (or `_₁,_₂,...`) may be used if you need more than one argument. Numbers indicate position in the argument list.
3. The double underscore placeholder `__` (and numbered versions `__1,__2,...`) expands the closure scope to the whole expression.
4. Piping and composition chains with `|>,<|,∘` are treated as a special case where the replacement recurses into sub-expressions.

These rules imply the following equivalences

| Expression                | Rules   | Meaning                       |
|:------------------------- |:------- |:----------------------------- |
| `@_ map(_+1, a)`          | (1)     | `map(x->x+1, a)`              |
| `@_ map(_^_, a)`          | (1)     | `map(x->x^x, a)`              |
| `@_ map(_2/_1, a, b)`     | (1,2)   | `map((x,y)->y/x, a, b)`       |
| `@_ func(a,__,b)`         | (3)     | `x->func(a,x,b)`              |
| `@_ func(a,__2,b)`        | (3)     | `(x,y)->func(a,y,b)`          |
| `@_ data \|> map(_.f,__)` | (1,3,4) | `data \|> (d->map(x->x.f,d))` |

# Extended help

## Examples

`@_` can be used for simple mapping operations in cases where broadcasting syntax is awkward. For example, to get the second last element of each array in a collection:

```jldoctest
julia> @_ map(_[end-1],  [[1,2,3], [4,5]])
2-element Vector{Int64}:
 2
 4
```

If you need to repeat an argument more than once, just use `_` multiple times:

```jldoctest
julia> @_ map(_^_,  [1,2,3])
3-element Vector{Int64}:
  1
  4
 27
```

For manipulating tabular data `@_` provides convenient syntax which is especially useful when combined with double underscore placeholders `__` and piping syntax. Think of `__` as the table, and `_` as an individual row:

```jldoctest
julia> table = [(x="a", y=1),
                (x="b", y=2),
                (x="c", y=3)];

julia> @_ table |>
          filter(!startswith(_.x, "a"), __) |>
          map(_.y, __)
2-element Vector{Int64}:
 2
 3
```

## Extraordinary functions

The scope of `_` as described in rule 1 depends on "ordinary" function call. This excludes the following operations:

  * Square brackets: In `map(_^2,__)[3]`, it is `map` which receives an anonymous function, as this happens before the indexing is lowered to `getindex(...,3)`. Comprehensions (`collect`) and explicit matrix constructions (`hvcat`) are treated similarly.
  * Broadcasting, and field access: In `f.(_,xs)` and `f(_,x).y` the function `f` is the ordinary call, not the internal `broadcast` or `getproperty`.
  * Infix operators: While `sum(_^2,x) / length(x)` can be written in prefix form `/(...,...)`, the convention of `@_` is not to view this as an ordinary call, and hence to pass the anonymous function to `sum` instead. This also applies to broadcasted operators, such as `map(_^2,x) ./ length(x)`.
  * If statements, including the ternary operator. Note that this has higher precedence than pipes: `data |> (any(_.x<0, __) ? abs.(__) : __) |> step` needs these brackets.

The scope of `__` is unaffected by these concerns.

| Expression                       | Meaning                             |
|:-------------------------------- |:----------------------------------- |
| `@_ data \|> map(_[2],__)[3]`    | `data \|> (d->map(x->x[2],d)[3])`   |
| `@_ [sum(_*_, z) for z in a]`    | `[sum(x->x*x, z) for z in a]`       |
| `@_ sum(1+_^2, data).re`         | `sum(x->1+x^2, data).re`            |
| `@_ sum(_^2,a) / length(a)`      | `sum(x->x^2,a) / length(a)`         |
| `@_ /(sum(_^2,a), length(a))`    | The same, infix form is canonical.  |
| `@_ data \|> filter(_>3,__).^2`  | `data \|> d->(filter(>(3),d).^2)`   |
| `@_ any(_>3,xs) ? 0 : map(_,ys)` | `any(x->x>3,xs) ? 0 : map(y->y,ys)` |
