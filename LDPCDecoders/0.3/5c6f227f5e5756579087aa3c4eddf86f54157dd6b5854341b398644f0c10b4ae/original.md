Function to batch decode given the parity check matrix, syndrome and errors

Scratch space allocations are done once and re-used for better performance

# Arguments

  * `decoder`: The Bit flip decoder configuration
  * `syndromes`: Syndrome matrix that contains batch syndromes
  * `errors`: Predefined error matrix that this function manipulates

# Examples

```jldoctest julia> decoder = BitFlipDecoder(LDPCDecoders.parity*check*matrix(1000, 10, 9), 0.01, 100);

julia> samples = 100

julia> errors = rand(1000,samples) .< 0.01;

julia> syndromes = zeros(900, samples);

julia> syndromes = H*errors .% 2

julia> guesses, successes = batchdecode!(decoder, syndromes, zero(errors));

julia> sum((guesses[:,i] == errors[:,i] for i in 1:samples)) > 0.995*samples
