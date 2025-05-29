```
run_verification_simulator(::TrustworthyServer, ::Terse, para)
```

Runs a verification simulator for a TrustworthyServer in a Terse mode. The function defines colouring, computes the backward flow, creates a client resource, draws random rounds, runs the verification, verifies the rounds, gets the mode output, and returns the verification results and mode outcome.

# Arguments

  * `::TrustworthyServer`: An instance of `TrustworthyServer`.
  * `::Terse`: An instance of `Terse`.
  * `para`: A dictionary containing the parameters for the verification simulator. It should include the keys `:graph`, `:input`, `:output`, `:secret_angles`, `:forward_flow`, `:total_rounds`, and `:computation_rounds`.

# Returns

  * A tuple containing the test verification result, the computation verification result, and the mode outcome.

# Examples

```julia
para = (args)::NamedTuple # function specific args
result = run_verification_simulator(TrustworthyServer(), Terse(), para)
```
