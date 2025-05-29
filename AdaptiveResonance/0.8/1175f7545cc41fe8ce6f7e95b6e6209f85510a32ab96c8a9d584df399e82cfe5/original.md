Main module for `AdaptiveResonance.jl`, a Julia package of adaptive resonance theory algorithms.

This module exports all of the ART modules, options, and utilities used by the `AdaptiveResonance.jl package.` For full usage, see the official guide at https://ap6yc.github.io/AdaptiveResonance.jl/dev/man/guide/.

# Basic Usage

Install and import the package in a script with

```julia
using Pkg
Pkg.add("AdaptiveResonance")
using AdaptiveResonance
```

then create an ART module with default options

```julia
my_art = DDVFA()
```

or custom options via keyword arguments

```julia
my_art = DDVFA(rho_ub=0.45, rho_ub=0.7)
```

Train all models with `train!` and conduct inference with `classify`. In batch, samples are interpreted in the Julia column-major fashion with dimensions `(n_dim, n_samples)` (i.e., columns are samples).

Train unsupervised ART modules incrementally or in batch with optional labels as a keyword argument `y`

```julia
# Load your data somehow
samples, labels = load_some_data()

# Unsupervised batch
train!(my_art, samples)

# Supervised batch
train!(my_art, samples, y=labels)

# Unsupervised incremental
for ix in eachindex(labels)
    train!(my_art, samples[:, ix])
end

# Supervised incremental
for ix in eachindex(labels)
    train!(my_art, samples[:, ix], y=labels[ix])
end
```

Train supervised ARTMAP with positional arguments

```julia
my_artmap = SFAM()
train!(my_artmap, samples, labels)
```

With either module, conduct inference with `classify(art, samples)`

```julia
# Batch inference
y_hat = classify(my_art, test_samples)

# Incremental inference
for ix in eachindex(test_labels)
    y_hat[ix] = classify(my_artmap, test_samples[:, ix])
end
```

# Imports

The following names are imported by the package as dependencies:

  * `Base`
  * `Core`
  * `Distributed`
  * `DocStringExtensions`
  * `ElasticArrays`
  * `Logging`
  * `NumericalTypeAliases`
  * `Parameters`
  * `Pkg`
  * `ProgressBars`
  * `SharedArrays`

# Exports

The following names are exported and available when `using` the package:

  * [`ACTIVATION_FUNCTIONS`](@ref)
  * [`ADAPTIVERESONANCE_MODULES`](@ref)
  * [`ADAPTIVERESONANCE_VERSION`](@ref)
  * [`ART`](@ref)
  * [`ARTMAP`](@ref)
  * [`ARTMAP_MODULES`](@ref)
  * [`ARTModule`](@ref)
  * [`ARTOpts`](@ref)
  * [`ART_MODULES`](@ref)
  * [`DAM`](@ref)
  * [`DDVFA`](@ref)
  * [`DDVFA_METHODS`](@ref)
  * [`DVFA`](@ref)
  * [`DataConfig`](@ref)
  * [`FAM`](@ref)
  * [`FuzzyART`](@ref)
  * [`GammaNormalizedFuzzyART`](@ref)
  * [`MATCH_FUNCTIONS`](@ref)
  * [`SFAM`](@ref)
  * [`UPDATE_FUNCTIONS`](@ref)
  * [`artscene_filter`](@ref)
  * [`classify`](@ref)
  * [`complement_code`](@ref)
  * [`data_setup!`](@ref)
  * [`get_W`](@ref)
  * [`get_data_characteristics`](@ref)
  * [`linear_normalization`](@ref)
  * [`opts_DAM`](@ref)
  * [`opts_DDVFA`](@ref)
  * [`opts_DVFA`](@ref)
  * [`opts_FAM`](@ref)
  * [`opts_FuzzyART`](@ref)
  * [`opts_GammaNormalizedFuzzyART`](@ref)
  * [`opts_SFAM`](@ref)
  * [`performance`](@ref)
  * [`train!`](@ref)
