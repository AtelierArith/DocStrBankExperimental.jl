```
diff_entropy_uniform(N::AbstractEcologicalNetwork, dims::I=nothing)
```

Computes the difference in entropy of the marginals compared to the entropy of an uniform distribution. The parameter `dims` indicates which marginals are used, with both if no value is provided. Output in bits.
