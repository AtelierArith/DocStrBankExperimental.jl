```
ttest(vec::AbstractVector{<:AbstractVector})
ttest(SB::AbstractVector, Sₜ::AbstractVector, SF::AbstractFloat)
```

# メソッド 1

```julia
ttest(vec::AbstractVector{<:AbstractVector})
```

`n` の値が平均 `x̄` とサンプル標準偏差 stddev を持ち、平均 $μ_0$ の分布から来ているという帰無仮説に対する一標本 t 検定を実行します。対立仮説は、その分布が平均 $μ_0$ を持たないことです。95% の信頼レベルの t 検定は、`vec` ベクトル内の各ベクトルのペアに適用されます。各ベクトルは、さまざまなデータセットにおける異なるアルゴリズムの年間パーセンテージ利回り (APY) を含む必要があります。

!!! note
    この関数を使用するには、`HypothesisTests` パッケージをインストールしてインポートする必要があります。


## 引数

  * `vec::AbstractVector{<:AbstractVector}`: ベクトルのベクトル。各内部ベクトルは同じサイズである必要があります。

## 戻り値

  * `::Matrix{<:AbstractFloat}`: 各アルゴリズムのペアに対する p 値の行列。

## 例

```julia
julia> using OnlinePortfolioSelection, HypothesisTests

julia> apys = [
         [1, 2, 3, 4],
         [2, 7, 0, 1],
         [3, 0, 0, 5]
       ];

julia> ttest(apys)
3×3 Matrix{Float64}:
 0.0  1.0  0.702697
 0.0  0.0  0.843672
 0.0  0.0  0.0
```

# メソッド 2

```julia
ttest(SB::AbstractVector, Sₜ::AbstractVector, SF::AbstractFloat)
```

トレーディングアルゴリズムによって得られたリターンが単なる運によるものであるかどうかを確認するために、t-スチューデント検定を実行します。

!!! note
    この関数を使用するには、`GLM` パッケージをインストールしてインポートする必要があります。


## 引数

  * `SB::AbstractVector`: ベンチマーク (市場指数) の日次リターンを示します
  * `Sₜ::AbstractVector`: ポートフォリオの日次リターン
  * `SF::AbstractFloat`: リスクフリー資産のデイリーリターン (国債の価値または年利率に設定できます。)
  * `::StatsModels.TableRegressionModel`: t-スチューデント検定分析の値を含む `TableRegressionModel` 型のオブジェクト。
