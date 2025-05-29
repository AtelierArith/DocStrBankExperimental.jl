```julia
StratMetropolisDist(smpl::ChronAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
```

サンプルの高さと `smpl` 構造体内のフィットした非対称年齢分布 (`BilinearExponential`) によって定義された層序サンプルのセットに対して、Chron.jl 年齢-深度モデルルーチンのメインを実行し、`config` 構造体によって定義された年齢-深度モデルの設定を行います。

オプションとして、`hiatus` 構造体が提供されると、モデルは指定されたモデルの高さでの既知の中断の期間に関する情報も組み込みます。

### 例:

```julia
(mdl, agedist, lldist) = StratMetropolisDist(smpl, config)
```

```julia
(mdl, agedist, hiatusdist, lldist) = StratMetropolisDist(smpl, hiatus, config)
```
