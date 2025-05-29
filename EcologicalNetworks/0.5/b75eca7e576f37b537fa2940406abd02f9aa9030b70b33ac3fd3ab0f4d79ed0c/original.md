```
linearfilter(N::BinaryNetwork, α::Vector{Float64}=[0.25, 0.25, 0.25, 0.25])
```

Given a network `N` compute the linear filter scores according to Stock et al. (2017). High scores for negative interactions indicate potential false negative or missing interactions. Though this it returned as a probabilistic network, score do not necessary convey a probabilistic interpretation.

The values of α give the *relative* weight of, in order, the measured interaction value, the out-degree of the species, the in-degree of the species, and of network connectance. The default parameterization is to have all four at equal importance.

#### References

Stock, M., Pahikkala, T., Airola, A., Waegeman, W., Baets, B.D., 2018. Algebraic Shortcuts for Leave-One-Out Cross-Validation in Supervised Network Inference. bioRxiv 242321. https://doi.org/10.1101/242321

Stock, M., Poisot, T., Waegeman, W., Baets, B.D., 2017. Linear filtering reveals false negatives in species interaction data. Scientific Reports 7, 45908. https://doi.org/10.1038/srep45908
