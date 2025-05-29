```
L0Smooth <: AbstractImageSmoothAlgorithm
L0Smooth(; λ=2e-2, κ=2.0, βmax=1e5)

smooth(img, f::L0Smooth)
smooth!(out, img, f::L0Smooth)
```

L0勾配最小化を通じて`img`を平滑化し、スパース制御の方法で顕著な構造を近似します。

# 出力

`Gray`入力の場合は`Array{Gray{N0f8}}`を、`RGB`入力の場合は`Array{RGB{N0f8}}`を返します。

# 詳細

画像の勾配のL0ノルムを最小化する戦略を使用しています。

このアルゴリズムは、主要なエッジをシャープにするのに特に効果的で、振幅遷移の急勾配を増加させる一方で、低振幅構造をある程度排除します。詳細については[1]を参照してください。

# オプション

関数の引数については以下に詳述します。

## `λ::Float64`

引数`𝜆`はL0勾配ノルム項の重要性を直接制御する重みで、ゼロより大きくなければなりません。

大きな`𝜆`は平滑化された画像に非常に少ないエッジを持たせます。

デフォルト: 2e-2

## `βmax::Float64`

引数`βmax`は[1]における`𝛽`の上限で、1e4より大きくなければなりません。

このアルゴリズムでは、2つの補助変数`ℎ`と`𝑣`を使用して解を近似します。十分に大きな`𝛽`は、補助変数を導入することに基づく交互最適化戦略が利用可能であることを保証します。

デフォルト: 1e5

## `κ::Float64`

引数`𝜅`は反復率で、1.0より大きくなければなりません。

このアルゴリズムは交互最適化戦略を使用して解を得ます。各反復において、引数`𝛽`は勾配ペア(𝛥₁𝑆ₚ, 𝛥₂𝑆ₚ)（[1]では$(\partial_x S_p, \partial_y S_p)$と表記）と補助ペア(ℎₚ, 𝑣ₚ)との類似性を制御します。引数`𝜅`は`𝛽`を`𝛽 ⟵ 𝜅𝛽`として更新するために使用されます。

デフォルト: 2.0

# 例

`L0Smooth`のデフォルト引数を使用し、次に`smooth`を使用して`AbstractImageSmoothAlgorithm`を適用できます。

```julia
using TestImages
using ImageSmooth

img = testimage("cameraman")

fₛ = L0Smooth() # デフォルト引数を使用
imgₛ = smooth(img, fₛ)
```

引数を手動で設定することも可能です：

```julia
fₛ = L0Smooth(λ=0.0015, κ=1.05, βmax=2e5) # 引数を手動で設定
imgₛ = smooth(img, fₛ)
```

インプレース操作については[`smooth!`](@ref)も参照してください。

# 参考文献

[1] Xu, L., Lu, C., Xu, Y., & Jia, J. (2011, December). Image smoothing via L 0 gradient minimization. In Proceedings of the 2011 SIGGRAPH Asia conference (pp. 1-12). [DOI:10.1145/2024156.2024208](https://doi.org/10.1145/2024156.2024208) ```
