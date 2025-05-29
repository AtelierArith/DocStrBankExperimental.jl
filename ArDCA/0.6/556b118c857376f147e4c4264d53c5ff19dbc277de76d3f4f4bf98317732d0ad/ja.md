```
sample(arnet::ArNet, msamples::Int)
```

生成されたアライメントを `N × msamples` の形式の `::Matrix{Int}` 型の行列として返します。

# 例

```
julia> arnet,arvar=ardca("file.fasta",verbose=true,permorder=:ENTROPIC, lambdaJ=0.001,lambdaH=0.001);
julia> Zgen=Zgen=sample(arnet,1000);
```
