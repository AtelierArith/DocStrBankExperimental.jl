```
greedycliquing(A::AbstractMatrix{Bool},  minsize::Int)
greedycliquing!(A::AbstractMatrix{Bool},  minsize::Int)
```

Greedy Cliquing Algorithm based off of: https://gitlab.invenia.ca/invenia/autopredictor/blob/develop/Tools/PreProcessing/GreedyCliquing.m

Splits an adjacency matrix into cliques [1] and remaining non-cliquable nodes. Compared to a previous version that acheives maximum node set reduction through optimal cliquing, this version finds a maximal clique, removes its nodes from the adjacency matrix, and repeats until no cliques can be found. More discussion can be found in this [2] Google doc.

[1] http://en.wikipedia.org/wiki/Clique*(graph*theory) [2] https://docs.google.com/a/invenia.ca/document/d/1lLRfQT*TFJi1bTfIu*jGxDs1u9A9HYKX5s4Zta3VRNg/edit?usp=sharing

# Arguments

  * `A::AbstractMatrix{Bool}`: Adjacency Matrix
  * `minsize::Int`: Min greedyclique size

# Returns

  * `cliques::Array{Clique}`: Vector array of type Clique
  * `singletons::Vector{Bool}`: Vector array of Bool. These indicate nodes not in a clique
