```
sample(arnet::ArNet, msamples::Int)
```

Return a generated alignment in the form of a `N × msamples`  matrix of type `::Matrix{Int}`  

# Examples

```
julia> arnet,arvar=ardca("file.fasta",verbose=true,permorder=:ENTROPIC, lambdaJ=0.001,lambdaH=0.001);
julia> Zgen=Zgen=sample(arnet,1000);
```
