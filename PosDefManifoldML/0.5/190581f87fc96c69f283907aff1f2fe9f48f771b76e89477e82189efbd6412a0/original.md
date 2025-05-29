```julia
function cvSetup(y            :: Vector{Int64},  
                 nCV          :: Int64;           
                 shuffle      :: Bool = false,
                 seed         :: Int = 1234)
```

Given a vector of labels `y` and a parameter `nCV`, this function generates indices for nCV-fold cross-validation sets, organized by class.

The function performs a stratified cross-validation by maintaining the same class distribution across all folds. This ensures that each fold contains approximately the same proportion of samples from each class as in the complete dataset.

Each element is used exactly once as a test sample across all folds, ensuring that the entire dataset is covered.

The `shuffle` parameter controls whether the indices within each class are randomized. When `shuffle` is false (default), the original sequence of indices is preserved, ensuring  consistent results across multiple executions.

When `shuffle`, is true the indices within each class are randomly permuted before creating  the cross-validation folds.  Randomization is controlled by the `seed` parameter (default: 1234).  Using the same `seed` value generates identical cross-validation sets. Using different `seed` values produce different random partitions.

This combination of `shuffle` and `seed` parameters allows you to generate reproducible random  splits for consistent experimentation, create different random partitions to assess the robustness  of your results and maintain exact reproducibility of your cross-validation experiments.

This function is used in [`crval`](@ref). It constitutes the fundamental basis to implement customized cross-validation procedures.

Return the 2-tuple (indTr, indTe) where:

  * indTr is an array of arrays where indTr[i][f] contains the training indices for class i in fold f
  * indTe is an array of arrays where indTe[i][f] contains the test indices for class i in fold f

Each array is organized by class and then by fold, ensuring stratified sampling across the cross-validation sets.

**Examples**

```julia
using PosDefManifoldML, PosDefManifold

y = [1,1,1,1,2,2,2,2,2,2]

cvSetup(y, 2)
# returns:
# Training Arrays:
#   Class 1: Array{Int64}[[3, 4], [1, 2]]
#   Class 2: Array{Int64}[[4, 5, 6], [1, 2, 3]]
# Testing Arrays:
#   Class 1: Array{Int64}[[1, 2], [3, 4]]
#   Class 2: Array{Int64}[[1, 2, 3], [4, 5, 6]]

cvSetup(y, 2; shuffle=true, seed=1)
# returns:
# Training Arrays:
#   Class 1: Array{Int64}[[1, 4], [2, 3]]
#   Class 2: Array{Int64}[[1, 3, 4], [2, 5, 6]]
# Testing Arrays:
#   Class 1: Array{Int64}[[2, 3], [1, 4]]
#   Class 2: Array{Int64}[[2, 5, 6], [1, 3, 4]]

cvSetup(y, 3)
# returns:
# Training Arrays:
#   Class 1: Array{Int64}[[2, 3], [1, 3, 4], [1, 2, 4]]
#   Class 2: Array{Int64}[[3, 4, 5, 6], [1, 2, 5, 6], [1, 2, 3, 4]]
# Testing Arrays:
#   Class 1: Array{Int64}[[1, 4], [2], [3]]
#   Class 2: Array{Int64}[[1, 2], [3, 4], [5, 6]]
```
