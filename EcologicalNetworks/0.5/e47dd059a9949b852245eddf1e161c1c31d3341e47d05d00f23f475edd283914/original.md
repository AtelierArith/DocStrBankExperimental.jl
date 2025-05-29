```
functional_cartography(N::T, L::Dict{E,Int64}) where {T<:BinaryNetwork, E}
```

This function will take the output of a modularity analysis (*i.e.* a network and a partition), and return a dictionary where every species is associated to its functional role, as defined in Olesen et al (2005). The first element is the within-module degree z-score, and the second is the participation coefficient.

#### References

Guimerà, R., Amaral, L.A.N., 2005. Cartography of complex networks: modules and universal roles. Journal of Statistical Mechanics: Theory and Experiment 2005, P02001. https://doi.org/10.1088/1742-5468/2005/02/P02001

Guimerà, R., Nunes Amaral, L.A., 2005. Functional cartography of complex metabolic networks. Nature 433, 895–900. https://doi.org/10.1038/nature03288

Olesen, J.M., Bascompte, J., Dupont, Y.L., Jordano, P., 2007. The modularity of pollination networks. Proceedings of the National Academy of Sciences 104, 19891–19896. https://doi.org/10.1073/pnas.0706375104
