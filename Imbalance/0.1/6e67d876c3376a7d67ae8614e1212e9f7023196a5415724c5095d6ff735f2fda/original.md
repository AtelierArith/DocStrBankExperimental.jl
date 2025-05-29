```
random_walk_oversample(
	X, y, cat_inds;
	ratios=1.0, rng=default_rng(),
	try_preserve_type=true
)
```

# Description

Oversamples a dataset using random walk oversampling as presented in [1]. 

# Positional Arguments

  * `X`: A matrix of floats or a table with element [scitypes](https://juliaai.github.io/ScientificTypes.jl/) that subtype `Union{Finite, Infinite}`.     Elements in nominal columns should subtype `Finite` (i.e., have scitype `OrderedFactor` or `Multiclass`) and    elements in continuous columns should subtype `Infinite` (i.e., have scitype `Count` or `Continuous`).
  * `y`: An abstract vector of labels (e.g., strings) that correspond to the observations in `X`
  * `cat_inds::AbstractVector{<:Int}`: A vector of the indices of the nominal features. Supplied only if `X` is a matrix.       Otherwise, they are inferred from the table's scitypes.

# Keyword Arguments

  * `ratios=1.0`: A parameter that controls the amount of oversampling to be done for each class

      * Can be a float and in this case each class will be oversampled to the size of the majority class times the float. By default, all classes are oversampled to the size of the majority class
      * Can be a dictionary mapping each class label to the float ratio for that class

  * `rng::Union{AbstractRNG, Integer}=default_rng()`: Either an `AbstractRNG` object or an `Integer`    seed to be used with `Xoshiro` if the Julia `VERSION` supports it. Otherwise, uses MersenneTwister`.

  * `try_preserve_type::Bool=true`: When `true`, the function will try to not change the type of the input    table (e.g., `DataFrame`). However, for some tables, this may not succeed, and in this case, the table returned will   be a column table (named-tuple of vectors). This parameter is ignored if the input is a matrix.

# Returns

  * `Xover`: A matrix or table that includes original data and the new observations    due to oversampling. depending on whether the input `X` is a matrix or table respectively
  * `yover`: An abstract vector of labels corresponding to `Xover`

# Example

```julia
using Imbalance
using ScientificTypes

# set probability of each class
class_probs = [0.5, 0.2, 0.3]                         
num_rows = 100
num_continuous_feats = 3
# want two categorical features with three and two possible values respectively
num_vals_per_category = [3, 2]

# generate a table and categorical vector accordingly
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, num_vals_per_category, rng=42)    
								                  
julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (39.6%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (68.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 

julia> ScientificTypes.schema(X).scitypes
(Continuous, Continuous, Continuous, Continuous, Continuous)
# coerce nominal columns to a finite scitype (multiclass or ordered factor)
X = coerce(X, :Column4=>Multiclass, :Column5=>Multiclass)

# apply random walk oversampling
Xover, yover = random_walk_oversample(X, y; 
                                      ratios = Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng = 42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJ Model Interface

Simply pass the keyword arguments while initiating the `RandomWalkOversampling` model and pass the  	positional arguments (excluding `cat_inds`) to the `transform` method. 

```julia
using MLJ
RandomWalkOversampler = @load RandomWalkOversampler pkg=Imbalance

# Wrap the model in a machine
oversampler = RandomWalkOversampler(ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# Provide the data to transform (there is nothing to fit)
Xover, yover = transform(mach, X, y)
```

You can read more about this `MLJ` interface by accessing it from MLJ's [model browser](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/). Note that only `Table` input is supported by the MLJ interface for this method.

# TableTransforms Interface

This interface assumes that the input is one table `Xy` and that `y` is one of the columns. Hence, an integer `y_ind` 	must be specified to the constructor to specify which column `y` is followed by other keyword arguments.  	Only `Xy` is provided while applying the transform.

```julia
using Imbalance
using ScientificTypes
using Imbalance.TableTransforms

# Generate imbalanced data
num_rows = 100
num_continuous_feats = 3
y_ind = 2

# generate a table and categorical vector accordingly
Xy, _ = generate_imbalanced_data(num_rows, num_continuous_feats; insert_y=y_ind,
                                class_probs= [0.5, 0.2, 0.3], num_vals_per_category=[3, 2],
                                 rng=42)  

# Table must have only finite or continuous scitypes                                
Xy = coerce(Xy, :Column2=>Multiclass, :Column5=>Multiclass, :Column6=>Multiclass)

# Initiate Random Walk Oversampler model
oversampler = RandomWalkOversampler(y_ind;
                                    ratios=Dict(1=>1.0, 2=> 0.9, 3=>0.9), rng=42)
Xyover = Xy |> oversampler                               
# equivalently if TableTransforms is used
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # equivalently
```

# Illustration

A full basic example along with an animation can be found [here](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_randomwalk.ipynb).      You may find more practical examples in the [tutorial](https://juliaai.github.io/Imbalance.jl/dev/examples/)      section which also explains running code on Google Colab.

# References

[1] Zhang, H., & Li, M. (2014). RWO-Sampling: A random walk over-sampling approach to imbalanced data classification.  Information Fusion, 25, 4-20.
