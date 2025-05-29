```
rose(
    X, y; 
    s=1.0, ratios=1.0, rng=default_rng(),
    try_preserve_type=true
)
```

# Description

Oversamples a dataset using `ROSE` (Random Oversampling Examples) algorithm to      correct for class imbalance as presented in [1]

# Positional Arguments

  * `X`: A matrix or table of floats where each row is an observation from the dataset
  * `y`: An abstract vector of labels (e.g., strings) that correspond to the observations in `X`

# Keyword Arguments

  * `s::float=1.0`: A parameter that proportionally controls the bandwidth of the Gaussian kernel
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

# set probability of each class
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 100, 5
# generate a table and categorical vector accordingly
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                class_probs, rng=42)  

julia> Imbalance.checkbalance(y)
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (39.6%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (68.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 

# apply ROSE
Xover, yover = rose(X, y; s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)

julia> Imbalance.checkbalance(yover)
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 38 (79.2%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 43 (89.6%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (100.0%) 
```

# MLJ Model Interface

Simply pass the keyword arguments while initiating the `ROSE` model and pass the      positional arguments `X, y` to the `transform` method. 

```julia
using MLJ
ROSE = @load ROSE pkg=Imbalance

# Wrap the model in a machine
oversampler = ROSE(s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
mach = machine(oversampler)

# Provide the data to transform (there is nothing to fit)
Xover, yover = transform(mach, X, y)
```

You can read more about this `MLJ` interface by accessing it from MLJ's [model browser](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/).

# TableTransforms Interface

This interface assumes that the input is one table `Xy` and that `y` is one of the columns. Hence, an integer `y_ind`     must be specified to the constructor to specify which column `y` is followed by other keyword arguments.      Only `Xy` is provided while applying the transform.

```julia
using Imbalance
using Imbalance.TableTransforms

# Generate imbalanced data
num_rows = 200
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                 class_probs=[0.5, 0.2, 0.3], insert_y=y_ind, rng=42)

# Initiate ROSE model
oversampler = ROSE(y_ind; s=0.3, ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
Xyover = Xy |> oversampler                              
# equivalently if TableTransforms is used
Xyover, cache = TableTransforms.apply(oversampler, Xy)    # equivalently
```

The `reapply(oversampler, Xy, cache)` method from `TableTransforms` simply falls back to `apply(oversample, Xy)` and the `revert(oversampler, Xy, cache)` reverts the transform by removing the oversampled observations from the table.

# Illustration

A full basic example along with an animation can be found [here](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/oversample_rose.ipynb).      You may find more practical examples in the [tutorial](https://juliaai.github.io/Imbalance.jl/dev/examples/)      section which also explains running code on Google Colab.

# References

[1] G Menardi, N. Torelli, “Training and assessing classification rules with imbalanced data,”  Data Mining and Knowledge Discovery, 28(1), pp.92-122, 2014.
