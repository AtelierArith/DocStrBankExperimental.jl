```julia
compile_algo(
    uai_filepath::AbstractString;
    uai_evid_filepath,
    td_filepath,
    apply_partial_evaluation,
    last_stage,
    smart_root_selection,
    factor_eltype,
    use_omeinsum,
    correct_fp_overflows
) -> Expr

```

Return an expression of the junction tree algorithm that extracts the marginals of all the variables in the model.

# Arguments

  * `uai_filepath::AbstractString`: path to the model file defined in the [UAI model file format](@ref).
  * `uai_evid_filepath::AbstractString = ""`: path to the evidence file defined in the [UAI evidence file format](@ref).
  * `td_filepath::AbstractString = ""`: path to a pre-constructed junction tree defined in the [PACE graph format](@ref).
  * `apply_partial_evaluation::Bool = false`: optimize the algorithm using partial evaluation.
  * `last_stage::LastStage = Marginals`: return an expression up to the given stage. The options are `ForwardPass`, `BackwardPass`, `JointMarginals`, `UnnormalizedMarginals` and `Marginals`.
  * `smart_root_selection::Bool = true`: select as root the cluster with the largest state space.
  * `factor_eltype::DataType = Float64`: type used to represent the factor values.
  * `use_omeinsum::Bool = false`: use the OMEinsum tensor network contraction package as backend for the factor operations.
  * `correct_fp_overflows::Bool = false`: normalize messages in the propagation phase that cause an overflow.

# Examples

```
package_root_dir = pathof(JunctionTrees) |> dirname |> dirname
uai_filepath = joinpath(package_root_dir, "docs", "src", "problems", "paskin", "paskin.uai")
algo = compile_algo(uai_filepath)
eval(algo)
obsvars, obsvals = Int64[], Int64[]
marginals = run_algo(obsvars, obsvals)

# output

6-element Vector{Factor{Float64, 1}}:
 Factor{Float64, 1}((1,), [0.33480077287635474, 0.33039845424729053, 0.33480077287635474])
 Factor{Float64, 1}((2,), [0.378700415763991, 0.621299584236009])
 Factor{Float64, 1}((3,), [0.3632859624875086, 0.6367140375124913])
 Factor{Float64, 1}((4,), [0.6200692707149191, 0.37993072928508087])
 Factor{Float64, 1}((5,), [0.649200314859223, 0.350799685140777])
 Factor{Float64, 1}((6,), [0.5968155611613972, 0.4031844388386027])
```

```
package_root_dir = pathof(JunctionTrees) |> dirname |> dirname
uai_filepath = joinpath(package_root_dir, "docs", "src", "problems", "paskin", "paskin.uai")
uai_evid_filepath = joinpath(package_root_dir, "docs", "src", "problems", "paskin", "paskin.uai.evid")
algo = compile_algo(
         uai_filepath,
         uai_evid_filepath = uai_evid_filepath)
eval(algo)
obsvars, obsvals = JunctionTrees.read_uai_evid_file(uai_evid_filepath)
marginals = run_algo(obsvars, obsvals)

# output

6-element Vector{Factor{Float64, 1}}:
 Factor{Float64, 1}((1,), [1.0, 0.0, 0.0])
 Factor{Float64, 1}((2,), [0.0959432982733719, 0.9040567017266281])
 Factor{Float64, 1}((3,), [0.07863089300137578, 0.9213691069986242])
 Factor{Float64, 1}((4,), [0.8440129077674895, 0.15598709223251056])
 Factor{Float64, 1}((5,), [0.9015456486772953, 0.09845435132270475])
 Factor{Float64, 1}((6,), [0.6118571666785584, 0.3881428333214415])
```
