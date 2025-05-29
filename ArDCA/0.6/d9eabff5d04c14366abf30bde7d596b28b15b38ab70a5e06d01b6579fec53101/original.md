```
sample_with_weights(arnet::ArNet, msamples::Int)
```

Return a generated alignment in the form of a `N × msamples`  matrix of type `::Matrix{Int}` and the relative probabilities under the module

# Examples

```
julia> arnet,arvar=ardca("file.fasta",verbose=true,permorder=:ENTROPIC, lambdaJ=0.001,lambdaH=0.001);
julia> Wgen,Zgen=sample_with_weights(arnet,1000);
```
