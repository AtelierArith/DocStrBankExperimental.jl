```
GeneratorParameterDistributions(number_of_states::Int; α=1, β=1, αs=ones(number_of_states - 1))
```

Gamma(α, 1/β)の事前分布を持つGeneratorParameterDistributionsオブジェクトを構築し、出口確率のためのDirichlet(αs)の事前分布を持ちます。各状態は同じ確率分布を持ちます。これは、事前分布を迅速に構築するのに便利です。デフォルトのレートに対する基本的な仮定は、時間の単位が1であるため、レートはすべてデフォルトで1であるということです。さらに、各状態の平均確率は1/(number*of*states-1)です。

αsの長さが(number*of*states - 1)である理由は、出口確率であり、したがって同じ状態に戻る確率は0であるためです。状態iの出口確率のインデックス順序は[1:i-1..., i+1:number*of*states...]です。例えば、number*of*states = 3の場合、状態1のインデックス順序はindices = [2, 3]であり、すなわち、indices[1] = 2およびindices[2] = 3であり、最初のインデックスは状態2を通じて退出することに対応し、2番目のインデックスは状態3を通じて退出することに対応します。状態2のインデックス順序はindices = [1, 3]であり、すなわち、indices[1] = 1およびindices[2] = 3であり、最初のインデックスは状態1を通じて退出することに対応し、2番目のインデックスは状態3を通じて退出することに対応します。状態3のインデックス順序はindices = [1, 2]であり、すなわち、indices[1] = 1およびindices[2] = 2であり、最初のインデックスは状態1を通じて退出することに対応し、2番目のインデックスは状態2を通じて退出することに対応します。

# 引数

  * `number_of_states::Int`: マルコフ連鎖の状態数。

# キーワード引数

  * `α::Number=2`: レートのGamma事前分布の形状パラメータ。
  * `β::Number=2`: レートのGamma事前分布のレートパラメータ。
  * `αs::Vector{Number}=ones(number_of_states - 1)`: 出口確率のDirichlet事前分布の濃度パラメータ。

# 戻り値

  * `GeneratorParameterDistributions`: レートのGamma(α, 1/β)事前分布と出口確率のDirichlet(αs)事前分布を持つGeneratorParameterDistributionsオブジェクト。

# Gamma事前分布に関する注意 (https://en.wikipedia.org/wiki/Gamma_distributionから)

Gamma分布は、レートの指数族分布に対する共役事前分布です。Gamma分布は、形状パラメータαとレートパラメータβによってパラメータ化されます。Gamma分布の平均はα/βであり、分散はα/β^2です。

# Dirichlet事前分布に関する注意 (https://en.wikipedia.org/wiki/Dirichlet_distributionから)

Dirichlet事前分布は、出口確率の多項分布に対する共役事前分布です。Dirichlet事前分布は、濃度パラメータαsによってパラメータ化されます。Dirichlet分布の平均はE[X⃗] = αs/sum(αs)であり、共分散はCoVar[X⃗ ⊗ X⃗] = Diagonal(α̃) - α̃ ⊗ α̃ / (α₀ + 1)であり、ここでα̃ = αs / α₀およびα₀ = sum(αs)です。分散Var(Xᵢ) = α̃ᵢ(1-α̃ᵢ) / (α₀ + 1)であり、ここでα₀ = sum(αs)です。 ```
