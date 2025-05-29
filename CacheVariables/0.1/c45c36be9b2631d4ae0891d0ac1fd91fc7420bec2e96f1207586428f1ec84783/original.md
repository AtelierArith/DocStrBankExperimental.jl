```
@cache path code [overwrite]
```

Cache results from running `code` using BSON file at `path`. Load if the file exists; run and save if it does not. Run and save either way if `overwrite` is true (default is false).

Tip: Use `begin...end` for `code` to cache blocks of code.

Caveat: The variable name `ans` is used for storing the final output, so it is best to avoid using it as a variable name in `code`.

# Examples

```julia-repl
julia> @cache "test.bson" begin
         a = "a very time-consuming quantity to compute"
         b = "a very long simulation to run"
         100
       end
┌ Info: Saving to test.bson
│ a
└ b
100

julia> @cache "test.bson" begin
         a = "a very time-consuming quantity to compute"
         b = "a very long simulation to run"
         100
       end
┌ Info: Loading from test.bson
│ a
└ b
100

julia> @cache "test.bson" begin
         a = "a very time-consuming quantity to compute"
         b = "a very long simulation to run"
         100
       end true
┌ Info: Overwriting test.bson
│ a
└ b
100
```
