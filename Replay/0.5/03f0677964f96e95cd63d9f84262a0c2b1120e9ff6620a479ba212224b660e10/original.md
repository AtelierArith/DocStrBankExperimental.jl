```
@deparse expr
```

Create a string from `expr`. It tries to output something similar to we type in Julia REPL. If `expr` contains `@comment <message>`, it is transformed into `# <message>`.

# Examples

```jldoctest
julia> @deparse 1+1
"1 + 1"

julia> @deparse sin(1f0+a)
"sin(1.0f0 + a)"

julia> @deparse f(x) = sin(x)/x  # Sometimes not work as expected
"f(x) = begin\n        sin(x) / x\n    end\n"
```
