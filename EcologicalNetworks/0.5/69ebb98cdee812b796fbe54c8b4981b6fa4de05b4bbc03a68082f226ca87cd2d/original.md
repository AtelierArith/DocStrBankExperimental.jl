```
lp(N::T) where {T<:AbstractEcologicalNetwork}
```

Uses label propagation to generate a first approximation of the modular structure of a network. This is usually followed by the BRIM (`brim`) method. This method supposedly performs better for large graphs, but we rarely observed any differences between it and variations of BRIM alone on smaller graphs.

#### References

Liu, X., Murata, T., 2009. Community Detection in Large-Scale Bipartite Networks, in: 2009 IEEE/WIC/ACM International Joint Conference on Web Intelligence and Intelligent Agent Technology. Institute of Electrical & Electronics Engineers (IEEE). https://doi.org/10.1109/wi-iat.2009.15
