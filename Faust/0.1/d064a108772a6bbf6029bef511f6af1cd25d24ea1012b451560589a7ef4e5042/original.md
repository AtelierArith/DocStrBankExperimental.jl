```
compile(code; name="score", argv=[], target="", opt=-1)
```

Compiles `code` to a `DSPBlock`.

# Arguments

  * `argv::Vector{String}`: List of args to the Faust compiler, e.g.   "-double": double precision   "-vec": vectorize code.
  * `target::String`: target for which to build LLVM IR. Defaults to current machine.
  * `opt::Integer`: -1 is "highest level available".

# Examples

```julia-repl
julia> d = compile("import("stdfaust.lib"); process = os.osc(freq) : *(0.25) <: _, _;")
```
