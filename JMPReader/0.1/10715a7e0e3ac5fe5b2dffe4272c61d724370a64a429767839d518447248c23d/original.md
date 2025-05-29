```
function readjmp(fn::AbstractString; select::Union{Nothing, Vector} = nothing; drop::Union{Nothing, Vector} = nothing)
```

Read a JMP file.

Included and excluded columns can be defined using keyword arguments `select` and `drop`. These are vectors defining columns with any combination of `Integer`, `OrdinalRange`, `String`, `Symbol`, `Regex`.

## Example

```
using JMPReader
fn = joinpath(pathof(JMPReader), "..", "..", "test", "example1.jmp")
df = readjmp(fn)
```
