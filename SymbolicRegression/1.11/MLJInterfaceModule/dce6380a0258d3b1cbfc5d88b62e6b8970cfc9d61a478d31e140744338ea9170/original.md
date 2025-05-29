```
MultitargetSRRegressor
```

A model type for constructing a Multi-Target Symbolic Regression via Evolutionary Search, based on [SymbolicRegression.jl](https://github.com/MilesCranmer/SymbolicRegression.jl), and implementing the MLJ model interface.

From MLJ, the type can be imported using

```
MultitargetSRRegressor = @load MultitargetSRRegressor pkg=SymbolicRegression
```

Do `model = MultitargetSRRegressor()` to construct an instance with default hyper-parameters. Provide keyword arguments to override hyper-parameter defaults, as in `MultitargetSRRegressor(defaults=...)`.

Multi-target Symbolic Regression regressor (`MultitargetSRRegressor`) conducts several searches for expressions that predict each target variable from a set of input variables. All data is assumed to be `Continuous`. The search is performed using an evolutionary algorithm. This algorithm is described in the paper https://arxiv.org/abs/2305.01582.

# Training data

In MLJ or MLJBase, bind an instance `model` to data with

```
mach = machine(model, X, y)
```

OR

```
mach = machine(model, X, y, w)
```

Here:

  * `X` is any table of input features (eg, a `DataFrame`) whose columns are of scitype

`Continuous`; check column scitypes with `schema(X)`. Variable names in discovered expressions will be taken from the column names of `X`, if available. Units in columns of `X` (use `DynamicQuantities` for units) will trigger dimensional analysis to be used.

  * `y` is the target, which can be any table of target variables whose element scitype is `Continuous`; check the scitype with `schema(y)`. Units in columns of `y` (use `DynamicQuantities` for units) will trigger dimensional analysis to be used.
  * `w` is the observation weights which can either be `nothing` (default) or an `AbstractVector` whose element scitype is `Count` or `Continuous`. The same weights are used for all targets.

Train the machine using `fit!(mach)`, inspect the discovered expressions with `report(mach)`, and predict on new data with `predict(mach, Xnew)`. Note that unlike other regressors, symbolic regression stores a list of lists of trained models. The models chosen from each of these lists is defined by the function `selection_method` keyword argument, which by default balances accuracy and complexity. You can override this at prediction time by passing a named tuple with keys `data` and `idx`.

# Hyper-parameters

  * `defaults`: What set of defaults to use for `Options`. The default,   `nothing`, will simply take the default options from the current version of SymbolicRegression.   However, you may also select the defaults from an earlier version, such as `v"0.24.5"`.
  * `binary_operators`: Vector of binary operators (functions) to use.   Each operator should be defined for two input scalars,   and one output scalar. All operators   need to be defined over the entire real line (excluding infinity - these   are stopped before they are input), or return `NaN` where not defined.   For speed, define it so it takes two reals   of the same type as input, and outputs the same type. For the SymbolicUtils   simplification backend, you will need to define a generic method of the   operator so it takes arbitrary types.
  * `operator_enum_constructor`: Constructor function to use for creating the operators enum.   By default, OperatorEnum is used, but you can provide a different constructor like   GenericOperatorEnum. The constructor must accept the keyword arguments 'binary*operators'   and 'unary*operators'.
  * `unary_operators`: Same, but for   unary operators (one input scalar, gives an output scalar).
  * `constraints`: Array of pairs specifying size constraints   for each operator. The constraints for a binary operator should be a 2-tuple   (e.g., `(-1, -1)`) and the constraints for a unary operator should be an `Int`.   A size constraint is a limit to the size of the subtree   in each argument of an operator. e.g., `[(^)=>(-1, 3)]` means that the   `^` operator can have arbitrary size (`-1`) in its left argument,   but a maximum size of `3` in its right argument. Default is   no constraints.
  * `batching`: Whether to evolve based on small mini-batches of data,   rather than the entire dataset.
  * `batch_size`: What batch size to use if using batching.
  * `elementwise_loss`: What elementwise loss function to use. Can be one of   the following losses, or any other loss of type   `SupervisedLoss`. You can also pass a function that takes   a scalar target (left argument), and scalar predicted (right   argument), and returns a scalar. This will be averaged   over the predicted data. If weights are supplied, your   function should take a third argument for the weight scalar.   Included losses:       Regression:           - `LPDistLoss{P}()`,           - `L1DistLoss()`,           - `L2DistLoss()` (mean square),           - `LogitDistLoss()`,           - `HuberLoss(d)`,           - `L1EpsilonInsLoss(ϵ)`,           - `L2EpsilonInsLoss(ϵ)`,           - `PeriodicLoss(c)`,           - `QuantileLoss(τ)`,       Classification:           - `ZeroOneLoss()`,           - `PerceptronLoss()`,           - `L1HingeLoss()`,           - `SmoothedL1HingeLoss(γ)`,           - `ModifiedHuberLoss()`,           - `L2MarginLoss()`,           - `ExpLoss()`,           - `SigmoidLoss()`,           - `DWDMarginLoss(q)`.
  * `loss_function`: Alternatively, you may redefine the loss used   as any function of `tree::AbstractExpressionNode{T}`, `dataset::Dataset{T}`,   and `options::AbstractOptions`, so long as you output a non-negative   scalar of type `T`. This is useful if you want to use a loss   that takes into account derivatives, or correlations across   the dataset. This also means you could use a custom evaluation   for a particular expression. If you are using   `batching=true`, then your function should   accept a fourth argument `idx`, which is either `nothing`   (indicating that the full dataset should be used), or a vector   of indices to use for the batch.   For example,

    ```
      function my_loss(tree, dataset::Dataset{T,L}, options)::L where {T,L}
          prediction, flag = eval_tree_array(tree, dataset.X, options)
          if !flag
              return L(Inf)
          end
          return sum((prediction .- dataset.y) .^ 2) / dataset.n
      end
    ```
  * `loss_function_expression`: Similar to `loss_function`, but takes `AbstractExpression` instead of `AbstractExpressionNode` as its first argument. Useful for `TemplateExpressionSpec`.
  * `loss_scale`: Determines how loss values are scaled when computing scores. Options are:

      * `:log` (default): Uses logarithmic scaling of loss ratios. This mode requires non-negative loss values   and is ideal for traditional loss functions that are always positive.
      * `:linear`: Uses direct differences between losses. This mode handles any loss values (including negative)   and is useful for custom loss functions, especially those based on likelihoods.
  * `expression_spec::AbstractExpressionSpec`: A specification of what types of expressions to use in the   search. For example, `ExpressionSpec()` (default). You can also see `TemplateExpressionSpec` and   `ParametricExpressionSpec` for specialized cases.
  * `populations`: How many populations of equations to use.
  * `population_size`: How many equations in each population.
  * `ncycles_per_iteration`: How many generations to consider per iteration.
  * `tournament_selection_n`: Number of expressions considered in each tournament.
  * `tournament_selection_p`: The fittest expression in a tournament is to be   selected with probability `p`, the next fittest with probability `p*(1-p)`,   and so forth.
  * `topn`: Number of equations to return to the host process, and to   consider for the hall of fame.
  * `complexity_of_operators`: What complexity should be assigned to each operator,   and the occurrence of a constant or variable. By default, this is 1   for all operators. Can be a real number as well, in which case   the complexity of an expression will be rounded to the nearest integer.   Input this in the form of, e.g., [(^) => 3, sin => 2].
  * `complexity_of_constants`: What complexity should be assigned to use of a constant.   By default, this is 1.
  * `complexity_of_variables`: What complexity should be assigned to use of a variable,   which can also be a vector indicating different per-variable complexity.   By default, this is 1.
  * `complexity_mapping`: Alternatively, you can pass a function that takes   the expression as input and returns the complexity. Make sure that   this operates on `AbstractExpression` (and unpacks to `AbstractExpressionNode`),   and returns an integer.
  * `alpha`: The probability of accepting an equation mutation   during regularized evolution is given by exp(-delta_loss/(alpha * T)),   where T goes from 1 to 0. Thus, alpha=infinite is the same as no annealing.
  * `maxsize`: Maximum size of equations during the search.
  * `maxdepth`: Maximum depth of equations during the search, by default   this is set equal to the maxsize.
  * `parsimony`: A multiplicative factor for how much complexity is   punished.
  * `dimensional_constraint_penalty`: An additive factor if the dimensional   constraint is violated.
  * `dimensionless_constants_only`: Whether to only allow dimensionless   constants.
  * `use_frequency`: Whether to use a parsimony that adapts to the   relative proportion of equations at each complexity; this will   ensure that there are a balanced number of equations considered   for every complexity.
  * `use_frequency_in_tournament`: Whether to use the adaptive parsimony described   above inside the score, rather than just at the mutation accept/reject stage.
  * `adaptive_parsimony_scaling`: How much to scale the adaptive parsimony term   in the loss. Increase this if the search is spending too much time   optimizing the most complex equations.
  * `turbo`: Whether to use `LoopVectorization.@turbo` to evaluate expressions.   This can be significantly faster, but is only compatible with certain   operators. *Experimental!*
  * `bumper`: Whether to use Bumper.jl for faster evaluation. *Experimental!*
  * `migration`: Whether to migrate equations between processes.
  * `hof_migration`: Whether to migrate equations from the hall of fame   to processes.
  * `fraction_replaced`: What fraction of each population to replace with   migrated equations at the end of each cycle.
  * `fraction_replaced_hof`: What fraction to replace with hall of fame   equations at the end of each cycle.
  * `should_simplify`: Whether to simplify equations. If you   pass a custom objective, this will be set to `false`.
  * `should_optimize_constants`: Whether to use an optimization algorithm   to periodically optimize constants in equations.
  * `optimizer_algorithm`: Select algorithm to use for optimizing constants. Default   is `Optim.BFGS(linesearch=LineSearches.BackTracking())`.
  * `optimizer_nrestarts`: How many different random starting positions to consider   for optimization of constants.
  * `optimizer_probability`: Probability of performing optimization of constants at   the end of a given iteration.
  * `optimizer_iterations`: How many optimization iterations to perform. This gets   passed to `Optim.Options` as `iterations`. The default is 8.
  * `optimizer_f_calls_limit`: How many function calls to allow during optimization.   This gets passed to `Optim.Options` as `f_calls_limit`. The default is   `10_000`.
  * `optimizer_options`: General options for the constant optimization. For details   we refer to the documentation on `Optim.Options` from the `Optim.jl` package.   Options can be provided here as `NamedTuple`, e.g. `(iterations=16,)`, as a   `Dict`, e.g. Dict(:x_tol => 1.0e-32,), or as an `Optim.Options` instance.
  * `autodiff_backend`: The backend to use for differentiation, which should be   an instance of `AbstractADType` (see `ADTypes.jl`).   Default is `nothing`, which means `Optim.jl` will estimate gradients (likely   with finite differences). You can also pass a symbolic version of the backend   type, such as `:Zygote` for Zygote, `:Enzyme`, etc. Most backends will not   work, and many will never work due to incompatibilities, though support for some   is gradually being added.
  * `perturbation_factor`: When mutating a constant, either   multiply or divide by (1+perturbation_factor)^(rand()+1).
  * `probability_negate_constant`: Probability of negating a constant in the equation   when mutating it.
  * `mutation_weights`: Relative probabilities of the mutations. The struct   `MutationWeights` (or any `AbstractMutationWeights`) should be passed to these options.   See its documentation on `MutationWeights` for the different weights.
  * `crossover_probability`: Probability of performing crossover.
  * `annealing`: Whether to use simulated annealing.
  * `warmup_maxsize_by`: Whether to slowly increase the max size from 5 up to   `maxsize`. If nonzero, specifies the fraction through the search   at which the maxsize should be reached.
  * `verbosity`: Whether to print debugging statements or   not.
  * `print_precision`: How many digits to print when printing   equations. By default, this is 5.
  * `output_directory`: The base directory to save output files to. Files   will be saved in a subdirectory according to the run ID. By default,   this is `./outputs`.
  * `save_to_file`: Whether to save equations to a file during the search.
  * `bin_constraints`: See `constraints`. This is the same, but specified for binary   operators only (for example, if you have an operator that is both a binary   and unary operator).
  * `una_constraints`: Likewise, for unary operators.
  * `seed`: What random seed to use. `nothing` uses no seed.
  * `progress`: Whether to use a progress bar output (`verbosity` will   have no effect).
  * `early_stop_condition`: Float - whether to stop early if the mean loss gets below this value.   Function - a function taking (loss, complexity) as arguments and returning true or false.
  * `timeout_in_seconds`: Float64 - the time in seconds after which to exit (as an alternative to the number of iterations).
  * `max_evals`: Int (or Nothing) - the maximum number of evaluations of expressions to perform.
  * `input_stream`: the stream to read user input from. By default, this is `stdin`. If you encounter issues   with reading from `stdin`, like a hang, you can simply pass `devnull` to this argument.
  * `skip_mutation_failures`: Whether to simply skip over mutations that fail or are rejected, rather than to replace the mutated   expression with the original expression and proceed normally.
  * `nested_constraints`: Specifies how many times a combination of operators can be nested. For example,   `[sin => [cos => 0], cos => [cos => 2]]` specifies that `cos` may never appear within a `sin`,   but `sin` can be nested with itself an unlimited number of times. The second term specifies that `cos`   can be nested up to 2 times within a `cos`, so that `cos(cos(cos(x)))` is allowed (as well as any combination   of `+` or `-` within it), but `cos(cos(cos(cos(x))))` is not allowed. When an operator is not specified,   it is assumed that it can be nested an unlimited number of times. This requires that there is no operator   which is used both in the unary operators and the binary operators (e.g., `-` could be both subtract, and negation).   For binary operators, both arguments are treated the same way, and the max of each argument is constrained.
  * `deterministic`: Use a global counter for the birth time, rather than calls to `time()`. This gives   perfect resolution, and is therefore deterministic. However, it is not thread safe, and must be used   in serial mode.
  * `define_helper_functions`: Whether to define helper functions   for constructing and evaluating trees.
  * `niterations::Int=10`: The number of iterations to perform the search.   More iterations will improve the results.
  * `parallelism=:multithreading`: What parallelism mode to use.   The options are `:multithreading`, `:multiprocessing`, and `:serial`.   By default, multithreading will be used. Multithreading uses less memory,   but multiprocessing can handle multi-node compute. If using `:multithreading`   mode, the number of threads available to julia are used. If using   `:multiprocessing`, `numprocs` processes will be created dynamically if   `procs` is unset. If you have already allocated processes, pass them   to the `procs` argument and they will be used.   You may also pass a string instead of a symbol, like `"multithreading"`.
  * `numprocs::Union{Int, Nothing}=nothing`:  The number of processes to use,   if you want `equation_search` to set this up automatically. By default   this will be `4`, but can be any number (you should pick a number <=   the number of cores available).
  * `procs::Union{Vector{Int}, Nothing}=nothing`: If you have set up   a distributed run manually with `procs = addprocs()` and `@everywhere`,   pass the `procs` to this keyword argument.
  * `addprocs_function::Union{Function, Nothing}=nothing`: If using multiprocessing   (`parallelism=:multithreading`), and are not passing `procs` manually,   then they will be allocated dynamically using `addprocs`. However,   you may also pass a custom function to use instead of `addprocs`.   This function should take a single positional argument,   which is the number of processes to use, as well as the `lazy` keyword argument.   For example, if set up on a slurm cluster, you could pass   `addprocs_function = addprocs_slurm`, which will set up slurm processes.
  * `heap_size_hint_in_bytes::Union{Int,Nothing}=nothing`: On Julia 1.9+, you may set the `--heap-size-hint`   flag on Julia processes, recommending garbage collection once a process   is close to the recommended size. This is important for long-running distributed   jobs where each process has an independent memory, and can help avoid   out-of-memory errors. By default, this is set to `Sys.free_memory() / numprocs`.
  * `worker_imports::Union{Vector{Symbol},Nothing}=nothing`: If you want to import   additional modules on each worker, pass them here as a vector of symbols.   By default some of the extensions will automatically be loaded when needed.
  * `runtests::Bool=true`: Whether to run (quick) tests before starting the   search, to see if there will be any problems during the equation search   related to the host environment.
  * `run_id::Union{String,Nothing}=nothing`: A unique identifier for the run.   This will be used to store outputs from the run in the `outputs` directory.   If not specified, a unique ID will be generated.
  * `loss_type::Type=Nothing`: If you would like to use a different type   for the loss than for the data you passed, specify the type here.   Note that if you pass complex data `::Complex{L}`, then the loss   type will automatically be set to `L`.
  * `selection_method::Function`: Function to selection expression from   the Pareto frontier for use in `predict`.   See `SymbolicRegression.MLJInterfaceModule.choose_best` for an example.   This function should return a single integer specifying   the index of the expression to use. By default, this maximizes   the score (a pound-for-pound rating) of expressions reaching the threshold   of 1.5x the minimum loss. To override this at prediction time, you can pass   a named tuple with keys `data` and `idx` to `predict`. See the Operations   section for details.
  * `dimensions_type::AbstractDimensions`: The type of dimensions to use when storing   the units of the data. By default this is `DynamicQuantities.SymbolicDimensions`.

# Operations

  * `predict(mach, Xnew)`: Return predictions of the target given features `Xnew`, which   should have same scitype as `X` above. The expression used for prediction is defined   by the `selection_method` function, which can be seen by viewing `report(mach).best_idx`.
  * `predict(mach, (data=Xnew, idx=i))`: Return predictions of the target given features   `Xnew`, which should have same scitype as `X` above. By passing a named tuple with keys   `data` and `idx`, you are able to specify the equation you wish to evaluate in `idx`.

# Fitted parameters

The fields of `fitted_params(mach)` are:

  * `best_idx::Vector{Int}`: The index of the best expression in each Pareto frontier, as determined by the `selection_method` function. Override in `predict` by passing a named tuple with keys `data` and `idx`.
  * `equations::Vector{Vector{Node{T}}}`: The expressions discovered by the search, represented in a dominating Pareto frontier (i.e., the best expressions found for each complexity). The outer vector is indexed by target variable, and the inner vector is ordered by increasing complexity. `T` is equal to the element type of the passed data.
  * `equation_strings::Vector{Vector{String}}`: The expressions discovered by the search, represented as strings for easy inspection.

# Report

The fields of `report(mach)` are:

  * `best_idx::Vector{Int}`: The index of the best expression in each Pareto frontier,  as determined by the `selection_method` function. Override in `predict` by passing  a named tuple with keys `data` and `idx`.
  * `equations::Vector{Vector{Node{T}}}`: The expressions discovered by the search, represented in a dominating Pareto frontier (i.e., the best expressions found for each complexity). The outer vector is indexed by target variable, and the inner vector is ordered by increasing complexity.
  * `equation_strings::Vector{Vector{String}}`: The expressions discovered by the search, represented as strings for easy inspection.
  * `complexities::Vector{Vector{Int}}`: The complexity of each expression in each Pareto frontier.
  * `losses::Vector{Vector{L}}`: The loss of each expression in each Pareto frontier, according to the loss function specified in the model. The type `L` is the loss type, which is usually the same as the element type of data passed (i.e., `T`), but can differ if complex data types are passed.
  * `scores::Vector{Vector{L}}`: A metric which considers both the complexity and loss of an expression, equal to the change in the log-loss divided by the change in complexity, relative to the previous expression along the Pareto frontier. A larger score aims to indicate an expression is more likely to be the true expression generating the data, but this is very problem-dependent and generally several other factors should be considered.

# Examples

```julia
using MLJ
MultitargetSRRegressor = @load MultitargetSRRegressor pkg=SymbolicRegression
X = (a=rand(100), b=rand(100), c=rand(100))
Y = (y1=(@. cos(X.c) * 2.1 - 0.9), y2=(@. X.a * X.b + X.c))
model = MultitargetSRRegressor(binary_operators=[+, -, *], unary_operators=[exp], niterations=100)
mach = machine(model, X, Y)
fit!(mach)
y_hat = predict(mach, X)
# View the equations used:
r = report(mach)
for (output_index, (eq, i)) in enumerate(zip(r.equation_strings, r.best_idx))
    println("Equation used for ", output_index, ": ", eq[i])
end
```

See also [`SRRegressor`](@ref).
