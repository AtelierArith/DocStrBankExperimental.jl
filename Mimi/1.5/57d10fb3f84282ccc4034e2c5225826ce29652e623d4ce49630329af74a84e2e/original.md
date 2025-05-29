```
Base.run(sim_def::SimulationDef{T}, 
        models::Union{Vector{M}, AbstractModel}, 
        samplesize::Int;
        ntimesteps::Int=typemax(Int), 
        trials_output_filename::Union{Nothing, AbstractString}=nothing, 
        results_output_dir::Union{Nothing, AbstractString}=nothing, 
        pre_trial_func::Union{Nothing, Function}=nothing, 
        post_trial_func::Union{Nothing, Function}=nothing,
        scenario_func::Union{Nothing, Function}=nothing,
        scenario_placement::ScenarioLoopPlacement=OUTER,
        scenario_args=nothing,
        results_in_memory::Bool=true) where {T <: AbstractSimulationData, M <: AbstractModel}
```

Run the simulation definition `sim_def` for the `models` using `samplesize` samples.

Optionally run the `models` for `ntimesteps`, if specified,  else to the maximum defined time period. Note that trial data are applied to all the  associated models even when running only a portion of them.   

If provided, the generated trials and results will be saved in the indicated  `trials_output_filename` and `results_output_dir` respectively. If `results_in_memory` is set to false, then results will be cleared from memory and only stored in the `results_output_dir`.

If `pre_trial_func` or `post_trial_func` are defined, the designated functions are called  just before or after (respectively) running a trial. The functions must have the signature:

```
fn(sim_inst::SimulationInstance, trialnum::Int, ntimesteps::Int, tup::Tuple)
```

where `tup` is a tuple of scenario arguments representing one element in the cross-product of all scenario value vectors. In situations in which you want the simulation loop to run only some of the models, the remainder of the runs can be handled using a `pre_trial_func` or `post_trial_func`.

If provided, `scenario_args` must be a `Vector{Pair}`, where each `Pair` is a symbol and a  `Vector` of arbitrary values that will be meaningful to `scenario_func`, which must have the signature:

```
scenario_func(sim_inst::SimulationInstance, tup::Tuple)
```

By default, the scenario loop encloses the simulation loop, but the scenario loop can be placed inside the simulation loop by specifying `scenario_placement=INNER`. When `INNER`  is specified, the `scenario_func` is called after any `pre_trial_func` but before the model is run.

Returns the type `SimulationInstance` that contains a copy of the original `SimulationDef`, along with mutated information about trials, in addition to the model list and  results information.
