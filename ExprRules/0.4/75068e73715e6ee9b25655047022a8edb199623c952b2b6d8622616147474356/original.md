```
@grammar
```

Define a grammar and return it as a Grammar. For example:

```julia-repl
grammar = @grammar begin
    R = x
    R = 1 | 2
    R = R + R
end
```
