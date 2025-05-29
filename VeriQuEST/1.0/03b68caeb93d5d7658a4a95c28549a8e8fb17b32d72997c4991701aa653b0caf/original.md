```
run_ubqc(para)
```

Runs a Universal Blind Quantum Computation (UBQC) using the provided parameters. The function creates a UBQC resource, generates a client meta graph, extracts the graph and quantum register (qureg) from the client, creates server resources, runs the computation, and gets the UBQC output.

# Arguments

  * `para`: A dictionary containing the parameters for the UBQC. It should include the key `:state_type`.

# Returns

  * The output of the UBQC, obtained by calling `get_ubqc_output`.

# Examples

```julia
para = (args)::NamedTuple # function specific args
ubqc_output = run_ubqc(para)
```
