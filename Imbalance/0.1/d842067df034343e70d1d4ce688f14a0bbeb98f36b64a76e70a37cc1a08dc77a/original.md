```
cluster_undersample(
    X, y; 
    mode= "nearest", ratios = 1.0, maxiter = 100,
    rng=default_rng(), try_preserve_type=true
)
```

# Description

Undersample a dataset using clustering undersampling as presented in [1] using K-means as the clustering algorithm.

# Positional Arguments

  * `X`: A matrix or table of floats where each row is an observation from the dataset
  * `y`: An abstract vector of labels (e.g., strings) that correspond to the observations in `X`

# Keyword Arguments

  * `mode::AbstractString="nearest`: If `"center"` then the undersampled data will consist of the centriods of    each cluster found; meanwhile, if `"nearest"` then it will consist of the nearest neighbor of each centroid.
  * `ratios=1.0`: A parameter that controls the amount of undersampling to be done for each class

      * Can be a float and in this case each class will be undersampled to the size of the minority class times the float. By default, all classes are undersampled to the size of the minority class
      * Can be a dictionary mapping each class label to the float ratio for that class

  * `maxiter::Integer=100`: Maximum number of iterations to run K-means
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
                                class_probs, rng=42)   
                                                    
julia> Imbalance.checkbalance(y; ref="minority")
 1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
 2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 33 (173.7%) 
 0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 48 (252.6%) 

# apply cluster_undersampling
X_under, y_under = cluster_undersample(X, y; mode="nearest", 
                                       ratios=Dict(0=>1.0, 1=> 1.0, 2=>1.0), rng=42)
                                       
julia> Imbalance.checkbalance(y_under; ref="minority")
0: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
2: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
1: ▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇▇ 19 (100.0%) 
```

# MLJ Model Interface

Simply pass the keyword arguments while initiating the `ClusterUndersampler` model and pass the      positional arguments `X, y` to the `transform` method. 

```julia
using MLJ
ClusterUndersampler = @load ClusterUndersampler pkg=Imbalance

# Wrap the model in a machine
undersampler = ClusterUndersampler(mode="nearest", 
                                   ratios=Dict(0=>1.0, 1=> 1.0, 2=>1.0), rng=42)
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
                                 class_probs=[0.5, 0.2, 0.3], insert_y=y_ind, rng=42)

# Initiate ClusterUndersampler model
undersampler = ClusterUndersampler(y_ind; mode="nearest", 
                                   ratios=Dict(0=>1.0, 1=> 0.9, 2=>0.8), rng=42)
Xy_under = Xy |> undersampler                    
Xy_under, cache = TableTransforms.apply(undersampler, Xy)    # equivalently
```

The `reapply(undersampler, Xy, cache)` method from `TableTransforms` simply falls back to `apply(undersample, Xy)` and the `revert(undersampler, Xy, cache)` is not supported.

# Illustration

A full basic example along with an animation can be found [here](https://githubtocolab.com/JuliaAI/Imbalance.jl/blob/dev/examples/undersample_cluster.ipynb).      You may find more practical examples in the [tutorial](https://juliaai.github.io/Imbalance.jl/dev/examples/)      section which also explains running code on Google Colab.

# References

[1] Wei-Chao, L., Chih-Fong, T., Ya-Han, H., & Jing-Shang, J. (2017).      Clustering-based undersampling in class-imbalanced data. Information Sciences, 409–410, 17–26.
