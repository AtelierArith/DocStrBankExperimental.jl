```julia
(1) function testCV(cv:CVresult, 
			expected::Union{Float64, Symbol} = :randomchance)

(2) function testCV(𝐂::Vector{Vector{Int}}; 
			expected::Union{Float64, Symbol} = :randomchance)

```

(1) Given a [`CVres`](@ref) stucture (which is of type `CVresult`) obtained calling the [`crval`](@ref) method,  performs Bayles's test (Bayles et *al.*, 2020[🎓](@ref))  on the difference in distribution of the average binary error losses obtained in the  cross-validation as compared to a given `expected` average error loss.  This can be used to test whether the performance obtained in the cross-validation is superior to a specified chance level.

(2) As method (1) but giving as first argument a vector of `f` confusion matrices,  The format of the confusion matrices (`Vector{Vector{Int}}`) is the same  used to store the confusion matrices in a [`CVres`](@ref) stucture.

The test is always directional. Denoting $μ$ the average loss and $E$ the expected average, the test if performed according to null hypethesis $H_0: μ1 = E$ against alternative $μ < E$; if the test is significant, the error loss is statistically inferior to the specified expected level, which means that the  observed accuracy is statistically **superior** to the expected accuracy.

By default, `expected` is set to $1-\frac{1}{z}$, where $z$ is the number of classes. You can pass another value, which must be a real number.

Return the 3-tuple (*z, p, ase*) holding, the $z$ test-statistic (a standard deviate),  the $p$-value and the asymptotic standard error.

!!! warning "Class Inbalance"
    The error lost reflects the accuracy, not the balance accuracy. If the class are inbalanced, the test will be driven by the majority classes. See also the documentation on [`crval`](@ref).


**Examples**:

```julia
using PosDefManifoldML

# Generate a set of random data
P, _dummyP, y, _dummyy = gen2ClassData(10, 60, 80, 30, 40, 0.1)

# Perform a cross-validation
cv = crval(MDM(Fisher), P, y; scoring=:a)

# The `z` and `p` values are printed out as they are computed automatically
# and stored in the created structure. To compute it yourself:

z, p, ase = testCV(cv)

```
