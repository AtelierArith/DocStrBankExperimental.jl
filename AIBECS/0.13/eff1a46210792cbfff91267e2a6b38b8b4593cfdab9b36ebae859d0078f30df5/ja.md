```
AbstractParameters{T} <: AbstractVector{T}
```

AIBECSモデルパラメータのための抽象型です。

AIBECSのパラメータは、以下の便利なパッケージを使用します：

  * Parameters
  * FieldMetadata
  * FieldDefaults
  * Flatten
  * Unitful
  * DataFrames
  * Distributions

これらは、以下のような素晴らしい機能を提供することを目的としています。

  * `@unpack`マクロ（UnPack.jlから）を介して関数内でパラメータをアンパックするための素晴らしい構文
  * パラメータに関する追加のメタデータ
  * ベクトルへの簡単な変換とその逆
  * 必要に応じて単位の使用と自動変換
  * 美しいテーブル形式の表示
  * CSVファイルへの読み込みと保存
  * ベイズ推論と最適化のための事前推定

モデルのパラメータを生成する方法のアイデアを得るために、例のリストを参照してください。

# 例

以下のようにシンプルなパラメータ型を生成します。

```jldoctest
julia> struct SimpleParams{T} <: AbstractParameters{T}
           α::T
           β::T
           γ::T
       end
SimpleParams
```

`SimpleParams(Float64)`型のインスタンスを作成するには、次のようにします。

```jldoctest
julia> p = SimpleParams(1.0, 2.0, 3.0)
SimpleParams{Float64}
│ Row │ Symbol │ Value   │
│     │ Symbol │ Float64 │
├─────┼────────┼─────────┤
│ 1   │ α      │ 1.0     │
│ 2   │ β      │ 2.0     │
│ 3   │ γ      │ 3.0     │
```

Parametersのコア機能の1つは、関数内でのアンパックです。例えば、

```jldoctest
julia> function simplef(p)
           @unpack α, γ = p
           return α + γ
       end
simplef (generic function with 1 method)

julia> simplef(p) # 1.0 + 3.0
4.0
```

メタデータを追加することで、より複雑な例が許可されます（FieldMetadata.jlのおかげです）。単位を追加できます。

```jldoctest
julia> @units struct UnitParams{T} <: AbstractParameters{T}
           α::T | u"km"
           β::T | u"hr"
           γ::T | u"m/s"
       end ;

julia> p = UnitParams(1.0, 2.0, 3.0)
UnitParams{Float64}
│ Row │ Symbol │ Value   │ Unit     │
│     │ Symbol │ Float64 │ Unitful… │
├─────┼────────┼─────────┼──────────┤
│ 1   │ α      │ 1.0     │ km       │
│ 2   │ β      │ 2.0     │ hr       │
│ 3   │ γ      │ 3.0     │ m s^-1   │
```

パラメータに単位を追加すると、アンパック時にSIに変換されることに注意してください。例えば、

```jldoctest
julia> function speed(p)
           @unpack α, β, γ = p
           return α / β + γ
       end
speed (generic function with 1 method)

julia> speed(p) # (1.0 km / 2.0 hr + 3 m/s) in m/s
3.138888888888889
```

最適化可能/フラット化可能なパラメータの別の例です。

```jldoctest
julia> @initial_value @units @flattenable struct OptParams{T} <: AbstractParameters{T}
           α::T | 3.6 | u"km"  | true
           β::T | 1.0 | u"hr"  | false
           γ::T | 1.0 | u"m/s" | true
       end ;

julia> p = OptParams(initial_value(OptParams)...)
OptParams{Float64}
│ Row │ Symbol │ Value   │ Initial value │ Unit     │ Optimizable │
│     │ Symbol │ Float64 │ Float64       │ Unitful… │ Bool        │
├─────┼────────┼─────────┼───────────────┼──────────┼─────────────┤
│ 1   │ α      │ 3.6     │ 3.6           │ km       │ 1           │
│ 2   │ β      │ 1.0     │ 1.0           │ hr       │ 0           │
│ 3   │ γ      │ 1.0     │ 1.0           │ m s^-1   │ 1           │
```

FieldMetaDataインターフェースのおかげで、以下の事前ロードされたメタデータをチェーンできます。

  * initial_value
  * units (Unitful.jlから)
  * prior (Distributions.jlから)
  * description (`String`)
  * bounds (2要素の`Tuple`)
  * logscaled (`Bool`)
  * flattenable (最適化可能なパラメータのベクトルに変換するため)
  * reference (`String`)

AIBECSで利用可能なすべてのメタデータを持つパラメータの例を示します。

```jldoctest
julia> @initial_value @units @prior @description @bounds @logscaled @flattenable @reference struct FullParams{T} <: AbstractParameters{T}
           α::T | 1.0 | u"km"  | Normal(0,1)    | "The distance"   | (-Inf, Inf) | false | false | "Jean et al., 2042"
           β::T | 2.0 | u"hr"  | LogNormal(0,1) | "The time"       | (   0, Inf) | true  | true  | "Claude et al. 1983"
           γ::T | 3.0 | u"mol" | Normal(1,2)    | "The # of moles" | (  -1,   1) | false | true  | "Dusse et al. 2000"
       end ;

julia> FullParams(4.0, 5.0, 6.0)
FullParams{Float64}
│ Row │ Symbol │ Value   │ Initial value │ Unit     │ Prior                            │ Description    │ Bounds      │ Logscaled │ Optimizable │ Reference          │
│     │ Symbol │ Float64 │ Float64       │ Unitful… │ Distribu…                        │ String         │ Tuple…      │ Bool      │ Bool        │ String             │
├─────┼────────┼─────────┼───────────────┼──────────┼──────────────────────────────────┼────────────────┼─────────────┼───────────┼─────────────┼────────────────────┤
│ 1   │ α      │ 4.0     │ 1.0           │ km       │ Normal{Float64}(μ=0.0, σ=1.0)    │ The distance   │ (-Inf, Inf) │ 0         │ 0           │ Jean et al., 2042  │
│ 2   │ β      │ 5.0     │ 2.0           │ hr       │ LogNormal{Float64}(μ=0.0, σ=1.0) │ The time       │ (0, Inf)    │ 1         │ 1           │ Claude et al. 1983 │
│ 3   │ γ      │ 6.0     │ 3.0           │ mol      │ Normal{Float64}(μ=1.0, σ=2.0)    │ The # of moles │ (-1, 1)     │ 0         │ 1           │ Dusse et al. 2000  │
```

提供されたメタデータが一貫しているかどうかのチェックは行われないことに注意してください。これらのメタデータは、AIBECSの高度な使用、例えば、最適化のための事前情報や境界を使用する際に役立つことを期待しています。
