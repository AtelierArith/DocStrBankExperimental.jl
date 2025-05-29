```
smoten(
    X, y;
    k=5, ratios=1.0, rng=default_rng(),
    try_preserve_type=true
)
```

# Description

Oversamples a dataset using `SMOTE-N` (Synthetic Minority Oversampling Techniques-Nominal) algorithm to      correct for class imbalance as presented in [1]. This is a variant of `SMOTE` to deal with datasets      where all features are nominal.

# Positional Arguments

  * `X`: A matrix of integers or a table with element [scitypes](https://juliaai.github.io/ScientificTypes.jl/) that subtype `Finite`.     That is, for table inputs each column should have either `OrderedFactor` or `Multiclass` as the element [scitype](https://juliaai.github.io/ScientificTypes.jl/).
  * `y`: An abstract vector of labels (e.g., strings) that correspond to the observations in `X`

# Keyword Arguments

  * `k::Integer=5`: Number of nearest neighbors to consider in the algorithm. Should be within the range `0 < k < n` where n is the number of observations in the smallest class.

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
num_continuous_feats = 0
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
(Count, Count)

# coerce to a finite scitype (multiclass or ordered factor)
X = coerce(X, autotype(X, :few_to_finite))

# apply SMOTEN
Xover, yover = smoten(X, y; k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJ Model Interface

Simply pass the keyword arguments while initiating the `SMOTEN` model and pass the      positional arguments `X, y` to the `transform` method. 

```julia
using MLJ
SMOTEN = @load SMOTEN pkg=Imbalance

# Wrap the model in a machine
oversampler = SMOTEN(k=5, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# Provide the data to transform (there is nothing to fit)
Xover, yover = transform(mach, X, y)
```

You can read more about this `MLJ` interface by accessing it from MLJ's [model browser](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/).

# TableTransforms Interface

This interface assumes that the input is one table `Xy` and that `y` is one of the columns. Hence, an integer `y_ind`     must be specified to the constructor to specify which column `y` is followed by other keyword arguments.      Only `Xy` is provided while applying the transform.

```julia
using Imbalance
using ScientificTypes
using Imbalance.TableTransforms

# Generate imbalanced data
num_rows = 100
num_continuous_feats = 0
y_ind = 2
# generate a table and categorical vector accordingly
Xy, _ = generate_imbalanced_data(num_rows, num_continuous_feats; insert_y=y_ind,
                                class_probs= [0.5, 0.2, 0.3], num_vals_per_category=[3, 2],
                                 rng=42)  

# Table must have only finite scitypes                                
Xy = coerce(Xy, :Column1=>Multiclass, :Column2=>Multiclass, :Column3=>Multiclass)

# Initiate SMOTEN model
oversampler = SMOTEN(y_ind; k=5, ratios=Dict(1=>1.0, 2=> 0.9, 3=>0.9), rng=42)
Xyover = Xy |> oversampler                               
# equivalently if TableTransforms is used
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # equivalently
```

The `reapply(oversampler, Xy, cache)` method from `TableTransforms` simply falls back to `apply(oversample, Xy)` and the `revert(oversampler, Xy, cache)` reverts the transform by removing the oversampled observations from the table.

# Illustration

A full basic example can be found [here](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_smoten.ipynb).      You may find more practical examples in the [tutorial](https://juliaai.github.io/Imbalance.jl/dev/examples/)      section which also explains running code on Google Colab.

# References

[1] N. V. Chawla, K. W. Bowyer, L. O.Hall, W. P. Kegelmeyer, “SMOTE: synthetic minority over-sampling technique,” Journal of artificial intelligence research, 321-357, 2002.
