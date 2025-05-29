```
flatmap(function_returning_A, a::A)::A
```

`flatmap` applies a function to a container and immediately flattens it out. While map would give you `A{A{...}}`, flatmap gives you a plain `A{...}`, without any nesting.

If you define your own versions of flatmap, the recommendation is to apply a `Base.convert` after applying `f`. This makes sure your flatmap is typesafe, and actually enables sound interactions with other types which may be convertable to your A.

E.g. for Vector the implementation looks as follows:

```
TypeClasses.flatmap(f, v::Vector) = vcat((convert(Vector, f(x)) for x in v)...)
```
