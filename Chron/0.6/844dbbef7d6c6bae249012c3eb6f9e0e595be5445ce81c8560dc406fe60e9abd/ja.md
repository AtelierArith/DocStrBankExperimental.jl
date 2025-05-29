```julia
StratMetropolis(smpl::ChronAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
StratMetropolis(smpl::GeneralAgeData, [hiatus::HiatusData,] config::StratAgeModelConfiguration)
```

主なChron.jl年齢-深度モデルルーチンを、サンプルの高さと`smpl`構造体内の単純なガウス年齢制約によって定義された堆積学的サンプルセットに対して実行します。また、`config`構造体によって定義された年齢-深度モデル構成を使用します。

オプションとして、`hiatus`構造体が提供される場合、モデルは指定されたモデルの高さでの既知の中断の期間に関する情報も組み込みます。

### 例:

```julia
(mdl, agedist, lldist) = StratMetropolis(smpl, config)
```

```julia
(mdl, agedist, hiatusdist, lldist) = StratMetropolis(smpl, hiatus, config)
```
