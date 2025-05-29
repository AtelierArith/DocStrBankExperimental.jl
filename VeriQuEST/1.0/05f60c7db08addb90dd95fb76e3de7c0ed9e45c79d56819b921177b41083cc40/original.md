```
run_verification_simulator(server::NoisyServer, ::Terse, para)
```

Runs a verification simulator on a `NoisyServer`. It defines colorings for computation and test rounds, computes the threshold for test rounds, creates a client resource, draws random rounds, runs the verification, verifies the rounds, and gets the mode outcome. Returns a tuple containing the results of the test verification, computation verification, and mode outcome.

# Arguments

  * `server::NoisyServer`: A `NoisyServer` instance on which the verification simulator will be run.
  * `::Terse`: A verbosity level for the verification process.
  * `para`: A dictionary containing parameters for the verification process.

# Returns

  * `Tuple`: A tuple containing the results of the test verification (`test_verification`), computation verification (`computation_verification`), and mode outcome (`mode_outcome`).

# Examples

```julia
server = NoisyServer(noise_model)
para = Dict(:graph => create_graph(Client(), 3), :input => Dict(:indices => [1, 2], :values => [0, 1]), :output => [3], :secret_angles => [0.5, 0.5], :forward_flow => [0.5, 0.5], :total_rounds => 10, :computation_rounds => 5, :state_type => :state1)
results = run_verification_simulator(server, Terse(), para)
```
