```
 @query expr
```

Creates a query object from a specialized path-like notation:

  * bare identifiers are translated to navigation with `Get`;
  * query combinators, such as `Count(X)`, use lower-case names;
  * the period (`.`) is used for query composition (`>>`);
  * aggregate queries, such as `Count`, require parentheses;
  * records can be constructed using curly brackets, `{}`; and
  * functions and operators are lifted automatically.

```jldoctest
julia> @query 2x+1
Lift(+, (Lift(*, (Lift(2), Get(:x))), Lift(1)))
```
