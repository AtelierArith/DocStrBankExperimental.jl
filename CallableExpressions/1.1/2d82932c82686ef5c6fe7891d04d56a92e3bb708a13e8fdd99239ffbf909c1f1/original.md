```
expression_into_type_domain(expression)
```

Returns an expression equal to `expression` whose data is completely contained in the type domain.

May throw in case Julia isn't able to use a relevant value as a type parameter.

Some properties, should hold for any valid `expr`:

  * `Base.issingletontype(typeof(expression_into_type_domain(expr)))`
  * `expr == expression_into_type_domain(expr)`
