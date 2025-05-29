```
posterior_samples_beta(modeloutput::SizeAndShapeModelOutput{KeepReflection,RL,P,DoNotRemoveSize,GramSchmidtMean,<:MCMCNormalDataKeepSize,<:LinearMean,<:MCMCLinearMean,CT,CM,PS}) where {
    RL<:RemoveLocation,
    CT<:TypeModelCoVariance,
    CM<:MCMCTypeModelCoVariance,
    PS<:MCMCObjectOUT,
    P<:ValueP   
}
```

The function extract the posterior sample of the regressive coefficients from an object of type `SizeAndShapeModelOutput` 
