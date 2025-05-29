```
@cast_str(code_string, delay=0, allow_errors=false) -> Cast
```

Creates a [`Cast`](@ref) object by executing the code in `code_string` in a REPL-like environment.

## Example

```julia
using Asciicast

c = cast"x=1"0.25 # note we set a delay of 0.25 here

Asciicast.save("test.cast", c)
```

To allow exceptions, one needs to invoke the macro manually on a string:

```julia
using Asciicast
c = @cast_str("error()", 0, true)
Asciicast.save("test.cast", c)
```
