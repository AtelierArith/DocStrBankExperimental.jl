```
qec_run_once(
    code, error_model, decoder, p::Real, rng::AbstractRNG=GLOBAL_RNG
) -> RunResult
```

Execute a stabilizer code error-decode-recovery (ideal) simulation and return run result.

The parameters `code`, `error_model` and `decoder` should be concrete subtypes or duck-typed implementations of [`StabilizerCode`](@ref), [`ErrorModel`](@ref) and [`Decoder`](@ref), respectively.

The simulation algorithm is as follows:

1. $S ←$ `stabilizers(code)`
2. $L ←$ `logicals(code)`
3. $e ←$ `generate(error_model, code, p, rng)`
4. $y ← S ⊙ e$
5. `decode_result` $←$ `decode(decoder, code,` $y$`; kwargs...)`
6. $r ←$ `decode_result.recovery`
7. sanity check: $S ⊙ (r ⊕ e) = 0$
8. `logical_commutations` $← L ⊙ (r ⊕ e)$
9. `success` $← L ⊙ (r ⊕ e) = 0$

where $⊕$ denotes element-wise exclusive-or, and $⊙$ is defined in [`PauliTools.bsp`](@ref bsp).

The `kwargs` passed to [`decode`](@ref) include `error_model`, `p` and `error`; most decoders will ignore these parameters. The [`decode`](@ref) method returns a [`DecodeResult`](@ref). If `decode_result.success` and/or `decode_result.logical_commutations` are specified, they override the values of `success` and `logical_commutations`, irrespective of whether `decode_result.recovery` is specified or not. The value `decode_result.custom_values` is passed through in the run result.

See also [`RunResult`](@ref).

# Examples

```jldoctest
julia> using Qecsim.BasicModels, Qecsim.GenericModels, Random

julia> rng = MersenneTwister(6);  # use random seed for reproducible result

julia> qec_run_once(FiveQubitCode(), DepolarizingErrorModel(), NaiveDecoder(), 0.2, rng)
RunResult{Nothing}(false, 2, Bool[1, 0], nothing)
```
