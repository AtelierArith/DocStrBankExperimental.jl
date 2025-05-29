Function to decode given the parity check matrix, syndrome and error

# Arguments

  * `decoder`: The Belief Propagation Decoder configuration
  * `syndrome`: Syndrome that is taken as input
  * `errors`: Predefined error array that this function manipulates

# Examples

```jldoctest
julia> H = LDPCDecoders.parity_check_matrix(1000, 10, 9);

julia> decoder = BeliefPropagationDecoder(H, 0.01, 100);

julia> error = rand(1000) .< 0.01;

julia> syndrome = (H * error) .% 2;

julia> guess, success = decode!(decoder, syndrome);

julia> error == guess
true
```
