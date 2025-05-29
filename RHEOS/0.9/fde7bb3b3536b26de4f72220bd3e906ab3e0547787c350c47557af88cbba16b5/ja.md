```
dynamicmodelfit(data::RheoFreqData, model::RheoModelClass; p0::Union{NamedTuple,Nothing} = nothing, lo::Union{NamedTuple,Nothing} = nothing, hi::Union{NamedTuple,Nothing} = nothing, verbose::Bool = false, rel_tol = 1e-4) where T<:Real
```

モデルを周波数/損失+貯蔵弾性率データにフィットさせます。

すべての引数は以下に説明されています。このフィッティング手順は、貯蔵弾性率と損失弾性率の2つの関数を同時にフィットさせるため、変換されていない場合、フィットは大きな絶対値を持つ弾性率を優先し、もう一方の弾性率をうまくフィットさせない傾向があります。これを避けるために、RHEOSは`weights`引数を変更することで使用できるいくつかのデータ変換を提供します。

# 引数

  * `data`: すべてのデータを含む`RheoFreqData`構造体
  * `model`: 弾性率とパラメータの記号を含む`RheoModelClass`
  * `p0`: フィットに使用する初期パラメータ（指定がない場合はすべてのパラメータに0.5を使用）
  * `lo`: パラメータの下限
  * `hi`: パラメータの上限
  * `verbose`: trueの場合、各最適化反復でパラメータを印刷
  * `rel_tol_x`: パラメータベクトルの最適化に対する相対許容誤差。詳細についてはNLOptのドキュメントを参照
  * `rel_tol_f`: 目的関数の最適化に対する相対許容誤差。詳細についてはNLOptのドキュメントを参照
  * `weights`: 貯蔵弾性率と損失弾性率の重み付けモード（`"none"`、`"mean"`、`"log"`、`"local"`または手動指定）
