```
@js win expr
```

Execute `expr`, converted to javascript, inside `win`, and return the result.

`expr` will be parsed as julia code, and then converted directly to the equivalent javascript. Language keywords that don't exist in julia can be represented with their macro equivalents, `@var`, `@new`, etc.

See also: `@js_`, the asynchronous version.

# Examples

```julia-repl
julia> @js win x = 5
5
julia> @js_ win for i in 1:x console.log(i) end
```
