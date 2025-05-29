```
RadialJohnsonSU(αinner, αouter)
```

正の単位半径のジョンソンSU分布によって与えられる放射プロファイルで、関数形式は次のとおりです。

```julia
    exp[-1/2(γ + arcsinh((r - μ)/σ)²]*inv(1 + (r - 1)² + σ²)
```

ここで、σ ≥ 0は幅を制御し、γは非対称性を制御します。

## ノート

これは通常、一般的なリングテンプレートを作成するために方位プロファイルと組み合わされます。

```julia-repl
julia> rad = RadialJohnsonSU(1/2, -3/2)
julia> azi = AzimuthalUniform()
julia> t = RingTemplate(rad, azi)
```

## 引数

  * `σ` : リングの幅
  * `γ` : リングの非対称性
