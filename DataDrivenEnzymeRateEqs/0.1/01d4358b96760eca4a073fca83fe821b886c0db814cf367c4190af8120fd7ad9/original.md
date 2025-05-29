```
data_driven_rate_equation_selection(
    general_rate_equation::Function,
    data::DataFrame,
    metab_names::Tuple{Symbol,Vararg{Symbol}},
    param_names::Tuple{Symbol,Vararg{Symbol}};
    range_number_params::Union{Nothing, Tuple{Int,Int}} = nothing,
    forward_model_selection::Bool = true,
    max_zero_alpha::Int = 1 + ceil(Int, length(metab_names) / 2),
    n_reps_opt::Int = 20,
    maxiter_opt::Int = 50_000,
    model_selection_method::String = "current_subsets_filtering",
    p_val_threshold::Float64 = 0.4,
    save_train_results::Bool = false,
    enzyme_name::String = "Enzyme",
    subsets_min_limit::Int = 1,
    subsets_max_limit::Union{Int, Nothing}=nothing,
    subsets_filter_threshold::Float64=0.1,
)
```

This function is used to perform data-driven rate equation selection using a general rate equation and data.

There are three model_selection methods:

1. current*subsets*filtering:

This method iteratively fits models that are subsets of the top 10% from the previous iteration, saving the best model for each n params based on training loss. Optimal number of parameters are selected using the Wilcoxon test on test scores from LOOCV, and the best equation is the best model with this optimal number.

2. cv*subsets*filtering:

This method implements current*subsets*filtering separately for each figure, leaving one figure out as a test set while training on the remaining data. For each number of parameters, it saves the test loss of the best subset for that figure. It uses the Wilcoxon test across all figures' results to select the optimal number of parameters. Then, for the chosen number, it trains all subset with this n params on the entire dataset and selects the best rate equation based on minimal training loss.

3. cv*all*subsets:

This method fits all subsets for each figure, using the others as training data and the left-out figure as the test set. It selects the best model for each number of parameters and figure based on training error and computes LOOCV test scores. The optimal n params is determined by the Wilcoxon test across all figures' test scores. The best equation is the subset with minimal training loss for this optimal n params when trained on the entire dataset.

# Arguments

  * `general_rate_equation::Function`: Function that takes a NamedTuple of metabolite concentrations (with `metab_names` keys) and parameters (with `param_names` keys) and returns an enzyme rate.
  * `data::DataFrame`: DataFrame containing the data with column `Rate` and columns for each `metab_names` where each row is one measurement. It also needs to have a column `source` that contains a string that identifies the source of the data. This is used to calculate the weights for each figure in the publication.
  * `metab_names::Tuple`: Tuple of metabolite names that correspond to the metabolites of `rate_equation` and column names in `data`.
  * `param_names::Tuple`: Tuple of parameter names that correspond to the parameters of `rate_equation`.

# Keyword Arguments

  * `save_train_results::Bool`: A boolean indicating whether to save the results of the training for each number of parameters as a csv file.
  * `enzyme_name::String`: A string for enzyme name that is used to name the csv files that are saved.
  * `range_number_params::Tuple{Int,Int}`: A tuple of integers representing the range of the number of parameters of general*rate*equation to search over.
  * `forward_model_selection::Bool`: A boolean indicating whether to use forward model selection (true) or reverse model selection (false).
  * `max_zero_alpha::Int`: An integer representing the maximum number of alpha parameters that can be set to 0.
  * `n_reps_opt::Int` n repetitions of optimization
  * `maxiter_opt::Int` max iterations of optimization algorithm
  * `model_selection_method::String` - which model selection to find best rate equation (default is current*subsets*filtering)
  * `p_val_threshold::Float64` - pval threshold for Wilcoxon test
  * `save_train_results::Bool`: A boolean indicating whether to save the results of the training for each number of parameters as a csv file.
  * `enzyme_name::String`: A string for enzyme name that is used to name the csv files that are saved.
  * `subsets_min_limit::Int` - The minimum number of filtered subsets (those with training loss within 10% of the minimum)

that must be kept for each number of parameters. These subsets are used to generate the subsets for the next iteration (only subsets of these are considered). Relevant to model selection methods current*subsets*filtering or cv*subsets*filtering.

  * `subsets_max_limit::Union{Int, Nothing}` - The maximum number of filtered subsets (those with training loss within 10% of the minimum)

that must be kept for each number of parameters. These subsets are used to generate the subsets for the next iteration (only subsets of these are considered). Relevant to model selection methods current*subsets*filtering or cv*subsets*filtering.

  * `subsets_filter_threshold::Float64` - This sets the percentage limit for filtering subsets in each iteration.

Only the subsets with a training loss close to the best (within this percentage) are kept.  Relevant to model selection methods current*subsets*filtering or cv*subsets*filtering.

# Returns

  * `NamedTuple`: A named tuple with the following fields:

      * `results`: df with train and test results
      * `best_n_params`: optimal number of parameters
      * `best_subset_row`: row of the best rate equation selected - includes fitted params
