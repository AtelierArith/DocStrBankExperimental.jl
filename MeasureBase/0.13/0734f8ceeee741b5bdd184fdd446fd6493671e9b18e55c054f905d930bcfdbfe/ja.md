```
Likelihood(k::AbstractTransitionKernel, x)
```

値 `x` を「観測」し、パラメータから ℝ への関数を生成します。

尤度は、既存の*事前*測度と組み合わせて新しい測度、すなわち*事後*を生成するために最も一般的に使用されます。ベイズの法則では、次のようになります。

$$
P(θ|x) ∝ P(θ) P(x|θ)
$$

ここで $P(θ)$ は事前です。$P(x|θ)$ を $θ$ に関する関数と考えると、それは尤度と呼ばれます。

測度は通常 `density` と `logdensity` を使用して操作されるため、(log-)尤度をどちらか一方にコミットするのは不便です。したがって、`Likelihood` を評価するためには、状況に応じて `density` または `logdensity` を使用します。後者の場合、もちろんそれはログ密度として機能します。

例えば、

```
julia> ℓ = Likelihood(Normal{(:μ,)}, 2.0)
Likelihood(Normal{(:μ,), T} where T, 2.0)

julia> density_def(ℓ, (μ=2.0,))
1.0

julia> logdensity_def(ℓ, (μ=2.0,))
-0.0
```

上記のように、測度がパラメータ情報を含む場合、`density` または `logdensity` への呼び出しの第二引数からそれを省略することができます。

```
julia> density_def(ℓ, 2.0)
1.0

julia> logdensity_def(ℓ, 2.0)
-0.0
```

複数のパラメータがある場合、期待通りに動作します：

```
julia> ℓ = Likelihood(Normal{(:μ,:σ)}, 2.0)
Likelihood(Normal{(:μ, :σ), T} where T, 2.0)

julia> logdensity_def(ℓ, (μ=2, σ=3))
-1.0986122886681098

julia> logdensity_def(ℓ, (2,3))
-1.0986122886681098

julia> logdensity_def(ℓ, [2, 3])
-1.0986122886681098
```

---

```
Likelihood(M<:ParameterizedMeasure, constraint::NamedTuple, x)
```

場合によっては、測度が複数のパラメータを持ち、それらの一部に関する (log-)尤度を求めたいことがあります。この場合、第二引数が制約である三引数形式を使用できます。例えば、

```
julia> ℓ = Likelihood(Normal{(:μ,:σ)}, (σ=3.0,), 2.0)
Likelihood(Normal{(:μ, :σ), T} where T, (σ = 3.0,), 2.0)
```

上記と同様に、次のようになります。

```
julia> density_def(ℓ, (μ=2.0,))
0.3333333333333333

julia> logdensity_def(ℓ, (μ=2.0,))
-1.0986122886681098

julia> density_def(ℓ, 2.0)
0.3333333333333333

julia> logdensity_def(ℓ, 2.0)
-1.0986122886681098
```

---

最後に、ベイズの法則の表現に戻りましょう。

$$
P(θ|x) ∝ P(θ) P(x|θ)
$$

右側の積は点ごとに計算されます。これを MeasureBase で扱うために、「点ごとの積」 `⊙` があり、測度と尤度を取り、新しい測度、すなわち事前の基準測度に対して密度 $P(θ) P(x|θ)$ を持つ非正規化事後を返します。

例えば、次のような場合を考えます。

```
μ ~ Normal()
x ~ Normal(μ,σ)
σ = 1
```

そして `x=3` を観測します。`μ` に対する事後測度を次のように計算できます。

```
julia> post = Normal() ⊙ Likelihood(Normal{(:μ, :σ)}, (σ=1,), 3)
Normal() ⊙ Likelihood(Normal{(:μ, :σ), T} where T, (σ = 1,), 3)

julia> logdensity_def(post, 2)
-2.5
```
