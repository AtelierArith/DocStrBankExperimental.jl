```
η(N::T, dims::Union{Nothing,Integer}=nothing) where {T <: Union{BipartiteNetwork, BipartiteProbaNetwork}}
```

ネットワークのマージンのネステッドネスをηを使用して返します。第二引数は`1`（行/上位レベルのネステッドネス）または`2`（列/下位レベルのネステッドネス）にすることができます。`nothing`のままにすると、ネットワーク全体のネステッドネスを測定します。

#### 参考文献

  * Bastolla, U., Fortuna, M.A., Pascual-García, A., Ferrera, A., Luque, B., Bascompte, J., 2009. 相互主義ネットワークの構造は競争を最小化し、生物多様性を高める。Nature 458, 1018–1020. https://doi.org/10.1038/nature07950
  * Poisot, T., Cirtwill, A.R., Cazelles, K., Gravel, D., Fortin, M.-J., Stouffer, D.B., 2016. 確率的ネットワークの構造。生態学と進化の方法 7, 303–312. https://doi.org/10.1111/2041-210X.12468
