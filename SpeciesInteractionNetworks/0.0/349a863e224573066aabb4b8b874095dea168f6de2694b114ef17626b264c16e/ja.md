```
randomdraws(N::SpeciesInteractionNetwork{<:Partiteness, <:Probabilistic})
```

確率的ネットワークからランダムに引き出すことによって*バイナリ*ネットワークを返します。各相互作用は独立したベルヌーイ試行と見なされます。

###### 参考文献

[Poisot2015structure](@citet*)
