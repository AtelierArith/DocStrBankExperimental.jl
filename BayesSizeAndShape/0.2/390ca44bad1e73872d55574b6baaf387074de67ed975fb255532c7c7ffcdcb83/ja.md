```
posterior_samples_beta(modeloutput::SizeAndShapeModelOutput{KeepReflection,RL,P,DoNotRemoveSize,GramSchmidtMean,<:MCMCNormalDataKeepSize,<:LinearMean,<:MCMCLinearMean,CT,CM,PS}) where {
    RL<:RemoveLocation,
    CT<:TypeModelCoVariance,
    CM<:MCMCTypeModelCoVariance,
    PS<:MCMCObjectOUT,
    P<:ValueP   
}
```

この関数は、`SizeAndShapeModelOutput` 型のオブジェクトから回帰係数の事後サンプルを抽出します。
