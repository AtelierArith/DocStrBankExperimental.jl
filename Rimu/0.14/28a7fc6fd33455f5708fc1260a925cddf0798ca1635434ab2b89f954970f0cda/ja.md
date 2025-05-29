```
AllOverlaps(n_replicas=2; operator=nothing, transform=nothing, vecnorm=true)
    <: ReplicaStrategy{n_replicas}
```

`n_replicas` 個のレプリカを実行し、すべてのレプリカベクトルのペア間のオーバーラップを報告します。`operator` が `nothing` でない場合、オーバーラップ `dot(c1, operator, c2)` も報告されます。`operator` がオペレーターのタプルである場合、すべてのオペレーターについてオーバーラップが計算されます。

レポートの列名は、ベクトル間のオーバーラップの場合は `c{i}_dot_c{j}` の形式で、オペレーター間のオーバーラップの場合は `c{i}_Op{k}_c{j}` の形式になります。

[`ProjectorMonteCarloProblem`](@ref)、[`ReplicaStrategy`](@ref)、および [`AbstractOperator`](@ref Interfaces.AbstractOperator)（オペレーターを実装するためのインターフェース）を参照してください。

# 変換されたハミルトニアン

変換されたハミルトニアン `G` が [`ProjectorMonteCarloProblem`](@ref) に渡された場合、同じ変換されたハミルトニアンを `AllOverlaps` に渡すことでオーバーラップを計算できます。この場合、`transform=G` を設定します。これらの2つのハミルトニアンが一致しない場合は警告が表示されます。

実装された変換は次のとおりです。

  * [`GutzwillerSampling`](@ref)
  * [`GuidingVectorSampling`](@ref)

変換されたハミルトニアンの場合、オーバーラップは次のように定義されます。ハミルトニアンの類似変換 `G` に対して（例：[`GutzwillerSampling`](@ref)を参照）。

$$
    \hat{G} = f \hat{H} f^{-1}.
$$

オペレーター $\hat{A}$ の期待値は

$$
    \langle \hat{A} \rangle = \langle \psi | \hat{A} | \psi \rangle
        = \frac{\langle \phi | f^{-1} \hat{A} f^{-1} | \phi \rangle}{\langle \phi | f^{-2} | \phi \rangle}
$$

であり、

$$
    | \phi \rangle = f | \psi \rangle
$$

は $\hat{G}$ の（右）固有ベクトルであり、$| \psi \rangle$ は $\hat{H}$ の固有ベクトルです。

入力オペレーターの K-タプル $(\hat{A}_1, ..., \hat{A}_K)$ に対して、$\langle \phi | f^{-1} \hat{A} f^{-1} | \phi \rangle$ のオーバーラップが `c{i}_Op{k}_c{j}` として報告されます。正しいベクトル間オーバーラップ $\langle \phi | f^{-2} | \phi \rangle$ は *最後* に `c{i}_Op{K+1}_c{j}` として報告されます。これは、*ベア* ベクトル間オーバーラップ $\langle \phi | f^{-2} | \phi \rangle$ が `c{i}_dot_c{j}` として報告されることに加えて行われます。

いずれの場合でも、`c{i}_dot_c{j}` オーバーラップはフラグ `vecnorm=false` を使用して省略できます。 ```
