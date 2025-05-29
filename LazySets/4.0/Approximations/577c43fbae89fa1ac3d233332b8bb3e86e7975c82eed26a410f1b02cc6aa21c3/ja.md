```
overapproximate(vTM::Vector{TaylorModel1{T, S}}, ::Type{<:Zonotope};
                [remove_redundant_generators]::Bool=true
                [normalize]::Bool=true) where {T, S}
```

1変数のテイラーモデルをゾノトープで過大評価します。

### 入力

  * `vTM`       – `TaylorModel1`のベクトル
  * `Zonotope`  –  対象セットタイプ
  * `remove_redundant_generators` – （オプション; デフォルト: `true`）結果のゾノトープの冗長な生成子を削除するフラグ
  * `normalize` – （オプション; デフォルト: `true`）テイラーモデルの正規化をスキップするフラグ

### 出力

与えられたテイラーモデルの範囲を過大評価するゾノトープ。

### 例

多項式が線形である場合、このメソッドは正確にゾノトープに変換します。非線形の場合は必然的に過大評価誤差が導入されます。まずは線形の場合を考えます：

```jldoctest oa_tm1
julia> using LazySets, TaylorModels

julia> const IA = IntervalArithmetic;

julia> I = IA.interval(-0.5, 0.5) # 区間残差
[-0.5, 0.5]

julia> x₀ = IA.interval(0.0) # 拡張点
[0, 0]

julia> D = IA.interval(-3.0, 1.0)
[-3, 1]

julia> p1 = Taylor1([2.0, 1.0], 2) # 線形多項式を定義
 2.0 + 1.0 t + 𝒪(t³)

julia> p2 = Taylor1([0.9, 3.0], 2) # 別の線形多項式を定義
 0.9 + 3.0 t + 𝒪(t³)

julia> vTM = [TaylorModel1(pi, I, x₀, D) for pi in [p1, p2]]
2-element Vector{TaylorModel1{Float64, Float64}}:
  2.0 + 1.0 t + [-0.5, 0.5]
  0.9 + 3.0 t + [-0.5, 0.5]
```

ここで、`vTM`はテイラーモデルベクトルであり、各成分は1変数のテイラーモデル（`TaylorModel1`）です。`overapproximate(vTM, Zonotope)`を使用して、その関連するゾノトープを生成子表現で計算できます：

```jldoctest oa_tm1
julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
2-element Vector{Float64}:
  1.0
 -2.1

julia> Matrix(genmat(Z))
2×3 Matrix{Float64}:
 2.0  0.5  0.0
 6.0  0.0  0.5
```

このゾノトープの生成子は主に2つの部分から構成されていることに注意してください：1つは多項式の線形部分から来ており、もう1つは区間残差に対応しています。この変換は、区間算術を使用した範囲評価と同じ上限と下限を提供します：

```jldoctest oa_tm1
julia> X = box_approximation(Z)
Hyperrectangle{Float64, Vector{Float64}, Vector{Float64}}([1.0, -2.1], [2.5, 6.5])

julia> Y = evaluate(vTM[1], vTM[1].dom) × evaluate(vTM[2], vTM[2].dom)
[-1.5, 3.5] × [-8.60001, 4.40001]

julia> H = convert(Hyperrectangle, Y) # このIntervalBoxはXと同じ
Hyperrectangle{Float64, StaticArraysCore.SVector{2, Float64}, StaticArraysCore.SVector{2, Float64}}([1.0, -2.1000000000000005], [2.5, 6.500000000000001])
```

ただし、ゾノトープはテイラーモデルを近似する場合、軸に沿っていないため、より良い結果を返します：

```jldoctest oa_tm1
julia> d = [-0.35, 0.93];

julia> ρ(d, Z) < ρ(d, X)
true
```

このメソッドは多項式が非線形である場合にも機能します。たとえば、3番目の多項式に2次項を追加すると仮定します：

```jldoctest oa_tm1
julia> p3 = Taylor1([0.9, 3.0, 1.0], 3)
 0.9 + 3.0 t + 1.0 t² + 𝒪(t⁴)

julia> vTM = [TaylorModel1(pi, I, x₀, D) for pi in [p1, p2, p3]]
3-element Vector{TaylorModel1{Float64, Float64}}:
           2.0 + 1.0 t + [-0.5, 0.5]
           0.9 + 3.0 t + [-0.5, 0.5]
  0.9 + 3.0 t + 1.0 t² + [-0.5, 0.5]

julia> Z = overapproximate(vTM, Zonotope);

julia> center(Z)
3-element Vector{Float64}:
  1.0
 -2.1
  2.4

julia> Matrix(genmat(Z))
3×4 Matrix{Float64}:
 2.0  0.5  0.0  0.0
 6.0  0.0  0.5  0.0
 6.0  0.0  0.0  5.0
```

最後の生成子は、区間残差と、ドメイン上の非線形部分の`p3`のボックス過大評価の加算に対応します。

### アルゴリズム

$$
\text{vTM} = (p, I)
$$

を$m$個のテイラーモデルのベクトルとし、$I$は$ℝ^m$における区間残差とします。$p_{lin}$（それぞれ$p_{nonlin}$）は各スカラー多項式の線形（それぞれ非線形）部分に対応します。

$$
\text{vTM}
$$

の範囲は、中心$c$と生成子行列$G$を持つゾノトープで囲むことができ、$Z = ⟨c, G⟩$は$\text{vTM}$の保守的な線形化を行うことによって得られます：

$$
    vTM' = (p', I') := (p_{lin} − p_{nonlin} , I + \text{Int}(p_{nonlin})).
$$

このアルゴリズムは2つのステップで進行します：

1- 上記のように$\text{vTM}$を保守的に線形化し、非線形部分のボックス過大評価を計算します。 2- 線形テイラーモデルを対称区間$[-1, 1]$への変数正規化を通じて正確にゾノトープに変換します。 ```
