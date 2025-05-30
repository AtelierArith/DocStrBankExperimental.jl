```
MMW{S} <: LowerBoundAlgorithm

MMW{1}() # min-d ヒューリスティック

MMW{2}() # max-d ヒューリスティック

MMW{3}() # least-c ヒューリスティック

MMW()
```

マイナー・ミン・ウィズスヒューリスティック。

```jldoctest
julia> using CliqueTrees

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

julia> alg = MMW{1}()
MMW{1}

julia> lowerbound(graph; alg)
2
```

# 参考文献

  * Gogate, Vibhav, and Rina Dechter. "A complete anytime algorithm for treewidth." *Proceedings of the 20th conference on Uncertainty in artificial intelligence.* 2004.
  * Bodlaender, Hans, Thomas Wolle, and Arie Koster. "Contraction and treewidth lower bounds." *Journal of Graph Algorithms and Applications* 10.1 (2006): 5-49.
