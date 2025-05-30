```
sigmapoints(m, Σ)
sigmapoints(d::Normal)
sigmapoints(d::MvNormal)
```

[無香変換](https://en.wikipedia.org/wiki/Unscented_transform#Sigma_points)は、確率密度の第一および第二モーメントを伝播させるために少数の点を使用します。これらの点を*シグマポイント*と呼びます。`sigmapoints(μ, Σ)`という関数を提供しており、これは`2n+1`のシグマポイントの`Matrix`を作成します。ここで、`n`は次元です。これは、任意の種類の`AbstractParticles`を初期化するために使用できます。例えば：

```julia
julia> m = [1,2]

julia> Σ = [3. 1; 1 4]

julia> p = StaticParticles(sigmapoints(m,Σ))
2-element Array{StaticParticles{Float64,5},1}:
 (5 StaticParticles: 1.0 ± 1.73)
 (5 StaticParticles: 2.0 ± 2.0)

julia> cov(p) ≈ Σ
true

julia> mean(p) ≈ m
true
```

スカラーの場合、`μ`と`Σ`を引数として渡す際には、分散（標準偏差ではなく）を第二引数として渡すことを確認してください。

# 注意

sigmapointsを独立して使用して複数の一次元の不確実な値を作成する場合、それらは強く相関します。多次元コンストラクタを使用してください！例：

```julia
p = StaticParticles(sigmapoints(1, 0.1^2))               # 誤り！
ζ = StaticParticles(sigmapoints(0.3, 0.1^2))             # 誤り！
ω = StaticParticles(sigmapoints(1, 0.1^2))               # 誤り！

p,ζ,ω = StaticParticles(sigmapoints([1, 0.3, 1], 0.1^2)) # 正しい
```
