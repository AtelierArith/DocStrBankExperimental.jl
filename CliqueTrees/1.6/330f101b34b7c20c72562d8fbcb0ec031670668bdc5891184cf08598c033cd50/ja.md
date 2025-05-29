```
SafeSeparators{M, A} <: EliminationAlgorithm

SafeSeparators(alg::EliminationAlgorithm, min::PermutationOrAlgorithm)

SafeSeparators(alg::EliminationAlgorithm)

SafeSeparators()
```

ほぼクリークセパレーター分解の原子に対して除去アルゴリズムを適用します。アルゴリズム `min` は分解を計算するために使用されます。

!!! warning
    アルゴリズム `min` は *最小* 順序を計算しなければなりません。この特性は以下のアルゴリズムによって保証されています：

      * [`MCSM`](@ref)
      * [`LexM`](@ref)
      * [`MinimalChordal`](@ref)


### パラメータ

  * `alg`: 除去アルゴリズム
  * `min`: 最小除去アルゴリズム

### 参考文献

  * Bodlaender, Hans L., and Arie MCA Koster. "Safe separators for treewidth." *Discrete Mathematics* 306.3 (2006): 337-350.
  * Tamaki, Hisao. "A heuristic for listing almost-clique minimal separators of a graph." arXiv preprint arXiv:2108.07551 (2021).
