```julia
    function saveas(object, filename::String)
```

Save the `object` to a file, which full path is given as `filemane`. It can be used, for instance, to save [`CVres`](@ref) structures and [`Pipeline`](@ref) tuples.

**See**: [`load`](@ref)

**Examples**

```julia
using PosDefManifoldML, PosDefManifold, Serialization

## Save and then load a cross-validation structure

P, _dummyP, y, _dummyy = gen2ClassData(10, 40, 40, 30, 40, 0.15)

cv = crval(MDM(logEuclidean), P, y; scoring=:a)

filename=joinpath(@__DIR__, "mycv.jls")
saveas(cv, filename)

mycv = load(filename)

# retrive the p-value of the cross-validation
mycv.p

## Save and then load a pipeline

# Generate some 'training' and `test` data
PTr=randP(3, 20) # 20 random 3x3 Hermitian matrices
PTe=randP(3, 5) # 5 random 3x3 Hermitian matrices

# fit a pipeline and transform the training data
p = fit!(PTr, @pipeline Recenter(; eVar=0.99) Compress)

# save the fitted pipeline
filename=joinpath(@__DIR__, "pipeline.jls")
saveas(p, filename) 

mypipeline = load(filename)

# transform the testing data using the loaded pipeline
transform!(PTe, mypipeline)
```
