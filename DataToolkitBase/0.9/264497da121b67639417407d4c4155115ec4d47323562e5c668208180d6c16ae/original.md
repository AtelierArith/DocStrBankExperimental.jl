```
prompt(question::AbstractString, default::AbstractString="",
       allowempty::Bool=false, cleardefault::Bool=true,
       multiline::Bool=false)
```

Interactively ask `question` and return the response string, optionally with a `default` value. If `multiline` is true, `RET` must be pressed twice consecutively to submit a value.

Unless `allowempty` is set an empty response is not accepted. If `cleardefault` is set, then an initial backspace will clear the default value.

The prompt supports the following line-edit-y keys:

  * left arrow
  * right arrow
  * home
  * end
  * delete forwards
  * delete backwards

### Example

```julia-repl
julia> prompt("What colour is the sky? ")
What colour is the sky? Blue
"Blue"
```
