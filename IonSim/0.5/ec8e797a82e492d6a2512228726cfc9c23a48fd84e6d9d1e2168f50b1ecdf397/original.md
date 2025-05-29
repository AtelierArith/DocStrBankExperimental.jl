```
quantumnumbers(I::Ion, level::String)
quantumnumbers(I::Ion, sublevel)
```

Returns the quantum numbers of an energy level or sublevel of `I` as a `NamedTuple`. If second argument is a level, returns `(:n, :i, :s, :l, :j, :f)` If second argument is a sublevel, returns `(:n, :i, :s, :l, :j, :f, :m)`
