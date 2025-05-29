```
predict(A::T, ytrain::T; GPU::Bool=false) where {T<:NamedMatrix}
```

Predict interactions between query and target nodes using *de novo* network-based inference model proposed by Wu, et al (2016).

# Arguments

  * `A::NamedMatrix`: Feature-source-target trilayered adjacency matrix
  * `ytrain::NamedMatrix`: Source-target bipartite adjacency matrix
  * `GPU::Bool`: Use GPU acceleration for calculation (default = false)

# References

1. Wu, et al (2016). SDTNBI: an integrated network and chemoinformatics tool for systematic prediction of drug–target interactions and drug repositioning. Briefings in Bioinformatics, bbw012. https://doi.org/10.1093/bib/bbw012
2. Vigil-Vásquez & Schüller (2022). De Novo Prediction of Drug Targets and Candidates by Chemical Similarity-Guided Network-Based Inference. International Journal of Molecular Sciences, 23(17), 9666. https://doi.org/10.3390/ijms23179666
