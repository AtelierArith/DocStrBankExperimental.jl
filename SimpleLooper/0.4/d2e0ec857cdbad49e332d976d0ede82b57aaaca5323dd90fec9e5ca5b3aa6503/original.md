```
@loop call
@loop n call
@loop bool_expr call
```

Repeat `call` indefinitely until interrupt or `n` times and discard the output. If an expression is given as a first argument it must return a `Bool` and repeats will occur until `false`.

```julia-repl
julia> @loop println("Hello, World!")
Hello, World!
Hello, World!^C
ERROR: InterruptException:
...

julia> @loop 2 println("Hello, World!")
Hello, World!
Hello, World!

julia> @loop rand() > 0.5 println("Hello, World!")
Hello, World!
```
