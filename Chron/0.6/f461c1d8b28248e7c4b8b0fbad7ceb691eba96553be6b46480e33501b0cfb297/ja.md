```julia
StratMetropolis14C(smpl::ChronAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
```

サンプルの高さと`smpl`構造体内の補間された放射性炭素年齢制約によって定義された堆積学的サンプルのセットに対して、Chron.jl年齢-深度モデルルーチンの主要な実行を行い、`config`構造体によって定義された年齢-深度モデルの構成を行います。

オプションとして、`hiatus`構造体が提供される場合、モデルは指定されたモデルの高さでの既知の中断の期間に関する情報も組み込みます。

### 例:

```julia
(mdl, agedist, lldist) = StratMetropolis14C(smpl, config)
```

```julia
(mdl, agedist, hiatusdist, lldist) = StratMetropolis14C(smpl, hiatus, config)
```
