```
OrthoMADS(N; search = NoSearch(), mesh = LogMesh(), reduction = NegReduction(N))
```

`poll = OrthoDirectionGenerator(N)`を持つ`MADS`オブジェクトを返します。ここで、`N`は問題の次元であり、`reduction`は[`NegReduction(N)`](@ref)または[`NoReduction()`](@ref)である可能性があります。NegReductionについては、Abramson et al. (2009)、ORTHOMADS、Audet et al. 2014を参照してください。
