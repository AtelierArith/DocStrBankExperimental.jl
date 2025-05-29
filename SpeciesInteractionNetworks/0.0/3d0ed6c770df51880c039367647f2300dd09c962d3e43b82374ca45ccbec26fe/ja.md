```
tsvd(N::SpeciesInteractionNetwork, r::Integer)
```

与えられた生態ネットワークの左および右の部分空間を返し、ランク `r` でのSVDの切り捨てを適用します。`r` がネットワークのランクよりも高い場合は、適切にスケーリングされます。

###### 参考文献

[DallaRiva2016Exploring](@citet*)
