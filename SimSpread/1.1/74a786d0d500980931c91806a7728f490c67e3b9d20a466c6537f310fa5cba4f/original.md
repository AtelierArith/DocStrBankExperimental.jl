```
spread(G::AbstractMatrix{Float64})
```

Calculate the transfer matrix for the adyacency matrix of the trilayered feature-source-target network.

# Arguments

  * `G::AbstractMatrix{Float64}`: Trilayered feature-source-target network adjacency matrix.

# Extended help

Potential interactions between nodes in a graph can be identified by using resource diffusion processes in the feature-source-target network, namely aforementioned graph `G`. For each node nᵢ in the network, it has initial resources located in both its neighboring nodes and its features. Initially, each feature and each neighboring node of nᵢ equally spread their resources to neighboring nodes. Subsequently, each of those nodes equally spreads its resources to neighbor nodes. Thus, nᵢ will obtain final resources located in several neighboring nodes, suggesting that nᵢ may have potential interactions with these nodes.

# References

1. Wu, et al (2016). SDTNBI: an integrated network and chemoinformatics tool for systematic prediction of drug–target interactions and drug repositioning. Briefings in Bioinformatics, bbw012. https://doi.org/10.1093/bib/bbw012
2. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
