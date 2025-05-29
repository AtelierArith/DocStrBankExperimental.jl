```
tomek_undersample(
    X, y;
    min_ratios = 1.0, force_min_ratios = false,
    rng = default_rng(), try_preserve_type=true
)
```

# Description

Undersample a dataset by removing ("cleaning") any point that is part of a tomek link in the data.  	Tomek links are presented in [1].

# Positional Arguments

  * `X`: A matrix or table of floats where each row is an observation from the dataset
  * `y`: An abstract vector of labels (e.g., strings) that correspond to the observations in `X`

# Keyword Arguments

  * `min_ratios=1.0`: A parameter that controls the maximum amount of undersampling to be done for each class. If this algorithm   cleans the data to an extent that this is violated, some of the cleaned points will be revived randomly so that it is satisfied.

      * Can be a float and in this case each class will be at most undersampled to the size of the minority class times the float. By default, all classes are undersampled to the size of the minority class
      * Can be a dictionary mapping each class label to the float minimum ratio for that class

  * `force_min_ratios=false`: If `true`, and this algorithm cleans the data such that the ratios for each class   exceed those specified in `min_ratios` then further undersampling will be perform so that the final ratios   are equal to `min_ratios`.

  * `rng::Union{AbstractRNG, Integer}=default_rng()`: Either an `AbstractRNG` object or an `Integer`    seed to be used with `Xoshiro` if the Julia `VERSION` supports it. Otherwise, uses MersenneTwister`.

  * `try_preserve_type::Bool=true`: When `true`, the function will try to not change the type of the input    table (e.g., `DataFrame`). However, for some tables, this may not succeed, and in this case, the table returned will   be a column table (named-tuple of vectors). This parameter is ignored if the input is a matrix.

# Returns

  * `X_under`: A matrix or table that includes the data after undersampling    depending on whether the input `X` is a matrix or table respectively
  * `y_under`: An abstract vector of labels corresponding to `X_under`

# Example

```julia
using Imbalance

# set probability of each class
class_probs = [0.5, 0.2, 0.3]                         
num_rows, num_continuous_feats = 100, 5
# generate a table and categorical vector accordingly
X, y = generate_imbalanced_data(num_rows, num_continuous_feats; 
                                min_sep=0.01, stds=[3.0 3.0 3.0], class_probs, rng=42)   

julia> Imbalance.checkbalance(y; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (173.7%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (252.6%) 

# apply tomek undersampling
X_under, y_under = tomek_undersample(X, y; min_ratios=1.0, rng=42)

julia> Imbalance.checkbalance(y_under; ref="minority")
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 22 (115.8%) 
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 36 (189.5%)
```

# MLJ Model Interface

Simply pass the keyword arguments while initiating the `TomekUndersampler` model and pass the      positional arguments `X, y` to the `transform` method. 

```julia
using MLJ
TomekUndersampler = @load TomekUndersampler pkg=Imbalance

# Wrap the model in a machine
undersampler = TomekUndersampler(min_ratios=1.0, rng=42)
mach = machine(undersampler)

# Provide the data to transform (there is nothing to fit)
X_under, y_under = transform(mach, X, y)
```

You can read more about this `MLJ` interface by accessing it from MLJ's [model browser](https://alan-turing-institute.github.io/MLJ.jl/dev/model_browser/).

# TableTransforms Interface

This interface assumes that the input is one table `Xy` and that `y` is one of the columns. Hence, an integer `y_ind`     must be specified to the constructor to specify which column `y` is followed by other keyword arguments.      Only `Xy` is provided while applying the transform.

```julia
using Imbalance
using Imbalance.TableTransforms

# Generate imbalanced data
num_rows = 100
num_features = 5
y_ind = 3
Xy, _ = generate_imbalanced_data(num_rows, num_features; 
                                min_sep=0.01, stds=[3.0 3.0 3.0], class_probs, rng=42)   

# Initiate TomekUndersampler model
undersampler = TomekUndersampler(y_ind; min_ratios=1.0, rng=42)
Xy_under = Xy |> undersampler                    
Xy_under, cache = TableTransforms.apply(undersampler, Xy)    # equivalently
```

The `reapply(undersampler, Xy, cache)` method from `TableTransforms` simply falls back to `apply(undersample, Xy)` and the `revert(undersampler, Xy, cache)` is not supported.

# Illustration

A full basic example along with an animation can be found [here](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/undersample_tomek.ipynb).      You may find more practical examples in the [tutorial](https://juliaai.github.io/Imbalance.jl/dev/examples/)      section which also explains running code on Google Colab.

# References

[1] Ivan Tomek. Two modifications of cnn. IEEE Trans. Systems, Man and Cybernetics, 6:769–772, 1976.
