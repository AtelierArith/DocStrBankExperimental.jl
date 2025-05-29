```
SAT{H, A} <: EliminationAlgorithm

SAT{H}(alg::PermutationOrAlgorithm)

SAT{H}()
```

SATソルバーを使用して最小ツリ幅の順列を計算します。

```julia-repl
julia> using CliqueTrees, libpicosat_jll, PicoSAT_jll, CryptoMiniSat_jll, Lingeling_jll

julia> graph = [
           0 1 0 0 0 0 0 0
           1 0 1 0 0 1 0 0
           0 1 0 1 0 1 1 1
           0 0 1 0 0 0 0 0
           0 0 0 0 0 1 1 0
           0 1 1 0 1 0 0 0
           0 0 1 0 1 0 0 1
           0 0 1 0 0 0 1 0
       ];

julia> alg = SAT{libpicosat_jll}(MF()) # picosat
SAT{libpicosat_jll, MF}:
    MF

julia> alg = SAT{PicoSAT_jll}(MF()) # picosat
SAT{PicoSAT_jll, MF}:
    MF

julia> alg = SAT{CryptoMiniSat_jll}(MF()) # cryptominisat
SAT{CryptoMiniSat_jll, MF}:
    MF

julia> alg = SAT{Lingeling_jll}(MMW(), MF()) # lingeling
SAT{Lingeling_jll, MF}:
    MF

julia> treewidth(graph; alg)
2
```

### パラメータ

  * `alg`: 除去アルゴリズム

## 参考文献

  * Samer, Marko, and Helmut Veith. "Encoding treewidth into SAT." *Theory and Applications of Satisfiability Testing-SAT 2009: 12th International Conference, SAT 2009*, Swansea, UK, June 30-July 3, 2009. Proceedings 12. Springer Berlin Heidelberg, 2009.
  * Berg, Jeremias, and Matti Järvisalo. "SAT-based approaches to treewidth computation: An evaluation." *2014 IEEE 26th international conference on tools with artificial intelligence.* IEEE, 2014.
  * Bannach, Max, Sebastian Berndt, and Thorsten Ehlers. "Jdrasil: A modular library for computing tree decompositions." *16th International Symposium on Experimental Algorithms (SEA 2017)*. Schloss Dagstuhl–Leibniz-Zentrum fuer Informatik, 2017.
