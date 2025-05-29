```
AutoSparse{D,S,C}
```

Wraps an ADTypes.jl object to deal with sparse Jacobians and Hessians.

# Fields

  * `dense_ad::D`: the underlying AD package, subtyping [`AbstractADType`](@ref)
  * `sparsity_detector::S`: the sparsity pattern detector, subtyping [`AbstractSparsityDetector`](@ref)
  * `coloring_algorithm::C`: the coloring algorithm, subtyping [`AbstractColoringAlgorithm`](@ref)

# Constructors

```
AutoSparse(
    dense_ad;
    sparsity_detector=ADTypes.NoSparsityDetector(),
    coloring_algorithm=ADTypes.NoColoringAlgorithm()
)
```
