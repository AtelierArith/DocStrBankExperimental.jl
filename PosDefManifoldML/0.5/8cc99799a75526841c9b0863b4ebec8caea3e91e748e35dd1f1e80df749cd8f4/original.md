```julia
function tsWeights(y::Vector{Int}; classWeights=[])
```

Given an [IntVector](@ref) of labels `y`, return a vector of weights summing up to 1 such that the overall weight is the same for all classes (balancing). This is useful for machine learning models in the tangent space with unbalanced classes for computing the mean, that is, the base point to map PD matrices onto the tangent space. For this mapping, giving equal weights to all observations actually overweights the larger classes and downweight the smaller classes.

Class labels for *n* classes must be the first *n* natural numbers, that is, `1` for class 1, `2` for class 2, etc. The labels in `y` can be provided in any order.

if a vector of *n* weights is specified as optional keyword argument `classWeights`, the overall weights for each class will be first balanced (see here above), then weighted by the `classWeights`. This allow user-defined control of weighting independently from the number of observations in each class. The weights in `classWeights` can be any integer or real non-negative numbers. The returned weight vector will nonetheless sum up to 1.

When you invoke the [`fit`](@ref) function for tangent space models you don't actually need this function, as you can invoke it implicitly passing symbol `:balanced` (or just `:b`) or a tuple with the class weights as optional keyword argument `w`.

**Examples**

```julia
# generate some data; the classes are unbalanced
PTr, PTe, yTr, yTe=gen2ClassData(10, 30, 40, 60, 80, 0.1)

# Fit an ENLR lasso model and find the best model by cross-validation
# balancing the weights for tangent space mapping
m=fit(ENLR(), PTr, yTr; w=tsWeights(yTr))

# A simpler syntax is
m=fit(ENLR(), PTr, yTr; w=:balanced)

# to balance the weights and then give overall weight 0.5 to class 1
# and 1.5 to class 2:
m=fit(ENLR(), PTr, yTr; w=(0.5, 1.5))

# which is equivalent to
m=fit(ENLR(), PTr, yTr; w=tsWeights(yTr; classWeights=(0.5, 1.5)))

```

This is how it works:

```julia
using PosDefManifoldML

# Suppose these are the labels:

y=[1, 1, 1, 1, 2, 2]

# We want the four observations of class 1 to count as much
# as the two observations of class 2.

tsWeights(y)

# 6-element Array{Float64,1}:
# 0.125
# 0.125
# 0.125
# 0.125
# 0.25
# 0.25

# i.e., 0.125*4 = 1.25*2
# and all weights sum up to 1

# Now, suppose we want to give to class 2 a weight
# four times bigger as compared to class 1:

tsWeights(y, classWeights=[1, 4])

# 6-element Array{Float64,1}:
# 0.05
# 0.05
# 0.05
# 0.05
# 0.4
# 0.4

# and, again, all weights sum up to 1.
```
