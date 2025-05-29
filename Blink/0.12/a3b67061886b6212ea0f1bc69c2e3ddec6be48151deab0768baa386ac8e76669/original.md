```
@js_ win expr
```

Execute `expr`, converted to javascript, asynchronously inside `win`, and return immediately.

`expr` will be parsed as julia code, and then converted directly to the equivalent javascript. Language keywords that don't exist in julia can be represented with their macro equivalents, `@var`, `@new`, etc.

See also: `@js`, the synchronous version that returns its result.

# Examples

```julia-repl
julia> @js win x = 5
5
julia> @js_ win for i in 1:x console.log(i) end
```
