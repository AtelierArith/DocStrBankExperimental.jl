```
@to_units f(x)
```

`f(x)`をUnitful単位で返します。測定単位は`default_units(a::typeof(f))`によって決定されます。

#例:

```julia-repl
julia> critical_pressure(water)
2.2064e7 Pa
```
