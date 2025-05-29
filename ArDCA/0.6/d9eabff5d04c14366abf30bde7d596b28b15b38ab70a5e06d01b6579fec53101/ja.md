```
sample_with_weights(arnet::ArNet, msamples::Int)
```

`::Matrix{Int}` 型の `N × msamples` 行列の形で生成されたアライメントとモジュールの下での相対確率を返します。

# 例

```
julia> arnet,arvar=ardca("file.fasta",verbose=true,permorder=:ENTROPIC, lambdaJ=0.001,lambdaH=0.001);
julia> Wgen,Zgen=sample_with_weights(arnet,1000);
```
