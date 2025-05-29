```
run_mbqc(para)
```

Runs a Measurement-Based Quantum Computation (MBQC) using the provided parameters. The function creates a UBQC resource, generates a client meta graph, extracts the quantum state from the client meta graph, runs the computation, and gets the output.

# Arguments

  * `para`: A dictionary containing the parameters for the MBQC. It should include the key `:state_type`.

# Returns

  * The output of the MBQC, obtained by calling `get_output`.

# Examples

```julia
para = (args)::NamedTuple # function specific args
mbqc_output = run_mbqc(para)
```
