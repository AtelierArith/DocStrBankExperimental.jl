```
qft(dimensions)
```

与えられた引数 `dimensions` に対して、[量子フーリエ変換 (QFT)](https://en.wikipedia.org/wiki/Quantum_Fourier_transform) の離散フーリエ変換行列 $\hat{F}_N$ を生成します。

`dimensions` は以下のいずれかの型であることができます：

  * `dimensions::Int`: ヒルベルト空間の基底状態の数。
  * `dimensions::Union{Dimensions,AbstractVector{Int},Tuple}`: 各サブシステムの基底の数を表す次元のリスト。

$$
N
$$

は総次元を表し、したがって行列は次のように定義されます。

$$
\hat{F}_N = \frac{1}{\sqrt{N}}\begin{bmatrix}
1 & 1 & 1 & 1 & \cdots & 1\\
1 & \omega & \omega^2 & \omega^3 & \cdots & \omega^{N-1}\\
1 & \omega^2 & \omega^4 & \omega^6 & \cdots & \omega^{2(N-1)}\\
1 & \omega^3 & \omega^6 & \omega^9 & \cdots & \omega^{3(N-1)}\\
\vdots & \vdots & \vdots & \vdots & \ddots & \vdots\\
1 & \omega^{N-1} & \omega^{2(N-1)} & \omega^{3(N-1)} & \cdots & \omega^{(N-1)(N-1)}
\end{bmatrix},
$$

ここで、$\omega = \exp(\frac{2 \pi i}{N})$ です。

!!! warning "型の安定性に注意！"
    `dimensions` を `Tuple` または [StaticArrays.jl](https://github.com/JuliaArrays/StaticArrays.jl) の `SVector` として `qft(dimensions)` を使用することを強く推奨します。型の安定性に関する詳細は、[関連セクション](@ref doc:Type-Stability) を参照してください。

