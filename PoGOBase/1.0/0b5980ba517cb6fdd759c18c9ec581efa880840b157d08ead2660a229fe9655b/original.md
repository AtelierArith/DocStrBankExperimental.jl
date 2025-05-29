```
megaevolve(poke::Pokemon, mega::Union{Bool, Char} = true) → megapoke
```

Create a new `Pokemon` object that is a mega-evolution of `poke`. If `mega` is `true`, the default mega-evolution is used. If `mega` is a `Char`, the mega-evolution with that name is used. If `mega` is `false`, the normal form is returned.
