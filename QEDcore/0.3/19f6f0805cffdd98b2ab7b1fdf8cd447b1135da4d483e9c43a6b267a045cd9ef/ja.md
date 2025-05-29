```
Boost{V<:QEDbase.AbstractBoostParameter} <: QEDbase.AbstractLorentzBoost
```

ローレンツブースト変換を表す具体的な型で、ブーストパラメータ `V` によってパラメータ化されています。ブーストパラメータは、使用される `QEDbase.AbstractBoostParameter` のサブタイプに応じて、軸特有またはベクトルのようなもののいずれかです。`Boost` 型は、特殊相対性理論における異なる慣性系間の四元ベクトル（四運動量や四位置など）にローレンツブーストを実行するために使用されます。

## フィールド

  * `param::V`: `AbstractBoostParameter` のサブタイプである型 `V` のブーストパラメータ。このパラメータは、速度（光速の割合としての $\beta$）とブーストの方向（例：単一の軸に沿ってまたは複数の方向に）を定義します。

## 概要

ローレンツブーストは、2つの基準フレーム間の相対速度に基づいて、四元ベクトルの時間成分と空間成分を調整する変換です。`Boost` 構造体は、そのようなブーストの一般的で柔軟な実装を提供し、ブーストパラメータの型がブーストの方向と大きさを決定します。

ブーストパラメータ `V` に応じて、ブーストは次のようになります：

  * **軸特有**: `V` が軸特有のブーストパラメータ（例：`BetaX`）である場合、ブーストはその軸に沿って行われます。
  * **ベクトルのような**: `V` がブーストパラメータのベクトル（例：`BetaVector`）である場合、ブーストは複数の空間方向に成分を持ちます。

## 例

`BetaX` ブーストパラメータを使用して x 軸に沿ったローレンツブーストを作成するには：

```jldoctest example_boost_x
julia> using QEDcore

julia> beta_x = BetaX(0.5)
BetaX{Float64}(0.5)

julia> boost_x = Boost(beta_x)
Boost{BetaX{Float64}}(BetaX{Float64}(0.5))
```

`boost_x` オブジェクトを使用してローレンツブーストを実行するには、四元ベクトル（四運動量など）に適用できます：

```jldoctest example_boost_x
julia> p = SFourMomentum(4, 3, 2, 1)
4-element SFourMomentum with indices SOneTo(4):
 4.0
 3.0
 2.0
 1.0

julia> p_prime = boost_x(p)  # ブーストを実行
4-element SFourMomentum with indices SOneTo(4):
 2.886751345948129
 1.1547005383792517
 2.0
 1.0

julia> @assert isapprox(p*p, p_prime*p_prime)  # 不変質量が保存される
```

## 注意事項

`Boost` 型は、ローレンツブーストを適用するための統一された柔軟なインターフェースを提供し、ブーストパラメータ `V` が変換の特定の形式を決定します。ローレンツブーストは時空間間隔を保存するため、四元ベクトルにブーストを適用しても不変量は変わりません。

## 参照

  * `QEDbase.AbstractBoostParameter`: 特定の種類のブーストパラメータのベース型。
  * [`BetaX`](@ref): x 軸のブーストパラメータ。
  * [`BetaY`](@ref): y 軸のブーストパラメータ。
  * [`BetaZ`](@ref): z 軸のブーストパラメータ。
  * [`BetaVector`](@ref): 複数の空間方向におけるブーストパラメータのベクトル。
