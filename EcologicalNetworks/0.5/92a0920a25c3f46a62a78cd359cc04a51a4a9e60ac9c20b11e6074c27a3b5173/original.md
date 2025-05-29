```
linearfilterzoo(N::BinaryNetwork, α::Vector{Float64}=[0.25, 0.25, 0.25, 0.25])
```

Compute the zero-one-out version of the linear filter (`linearfilter`), i.e. the score for each interaction if that interaction would not occur in the network. For example, if N[4, 6] = 1 (interaction between species 4 and 6), the result at postion (4, 6) is the score of the filter using a network in which that interaction did not occur. This function is useful for validating the filter whether it can detect false negative (missing) interactions.

#### References

Stock, M., Pahikkala, T., Airola, A., Waegeman, W., Baets, B.D., 2018. Algebraic Shortcuts for Leave-One-Out Cross-Validation in Supervised Network Inference. bioRxiv 242321. https://doi.org/10.1101/242321

Stock, M., Poisot, T., Waegeman, W., Baets, B.D., 2017. Linear filtering reveals false negatives in species interaction data. Scientific Reports 7, 45908. https://doi.org/10.1038/srep45908
