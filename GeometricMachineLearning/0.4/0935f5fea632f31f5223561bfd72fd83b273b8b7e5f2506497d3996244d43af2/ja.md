```
VolumePreservingFeedForwardLayer <: AbstractExplicitLayer
```

[`VolumePreservingLowerLayer`](@ref) と [`VolumePreservingUpperLayer`](@ref) のスーパタイプです。レイヤーは次のように動作します：

$$
x \mapsto \begin{cases} \sigma(Lx + b) & \text{ここで $L$ は }\mathtt{LowerTriangular}, \\ \sigma(Ux + b) & \text{ここで $U$ は }\mathtt{UpperTriangular}. \end{cases}
$$

ファンクタはベクトル、行列、またはテンソルに適用できます。特別な行列は [`LowerTriangular`](@ref) と [`UpperTriangular`](@ref) として実装されています。
