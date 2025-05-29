```
@f_str(string::AbstractString)

Loose implementation of Python style `fstring` literal string interpolation 
based on `Printf.@sprintf`.
```

# Examples

```julia-repl
julia> using FStrings
julia> f"π ≈ {π:.2f}"
"π ≈ 3.14"
```

# Format Specifiers

Please refer to `Printf.@sprintf` for further details on the available format specifiers. Also refer to the principle syntax of `fstring` via PEP 498.

# References

  * [`Printf.@sprintf`]: https://docs.julialang.org/en/v1/stdlib/Printf/#Printf.@sprintf
  * [PEP 498]: https://www.python.org/dev/peps/pep-0498/
