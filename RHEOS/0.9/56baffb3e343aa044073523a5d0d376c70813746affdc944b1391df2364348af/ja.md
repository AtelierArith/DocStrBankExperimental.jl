```
modelstepfit(data::RheoTimeData, model::RheoModelClass, modloading::Union{LoadingType,Integer}; step=nothing, p0::Union{NamedTuple,Nothing} = nothing, lo::Union{NamedTuple,Nothing} = nothing, hi::Union{NamedTuple,Nothing} = nothing, verbose::Bool = false, rel_tol_x = 1e-4, weights::Union{Vector{Integer},Nothing} = nothing)
```

`modelfit`と同様ですが、ステップ荷重を仮定します。この仮定がデータに適している場合、この関数を使用することでフィッティングを大幅に高速化できます。`modloading`が`strain_imposed`の場合、緩和弾性率が使用され、ひずみの中央の要素がステップの振幅であると仮定されます。`modloading`が`stress_imposed`の場合、クリープ弾性率が使用され、応力の中央の要素がステップの振幅であると仮定されます。あるいは、オプションの`step`パラメータを定義することでステップの値を定義することも可能です。

# 引数

  * `data`: すべてのデータを含む`RheoTimeData`構造体
  * `model`: 弾性率とパラメータのタプルを含む`RheoModelClass`
  * `modloading`: 緩和弾性率の場合は`strain_imposed`、クリープ弾性率の場合は`stress_imposed`
  * `step`: ステップのオプションの振幅
  * `p0`: フィッティングに使用する初期パラメータの名前付きタプル（指定がない場合はすべてのパラメータに0.5を使用）
  * `lo`: パラメータの下限の名前付きタプル
  * `hi`: パラメータの上限の名前付きタプル
  * `verbose`: trueの場合、各最適化反復でパラメータを印刷
  * `rel_tol_x`: 入力パラメータ値の関数としての最適化の相対許容誤差。詳細はNLOptのドキュメントを参照
  * `rel_tol_f`: 指定された場合、デフォルトの最適化停止基準をオーバーライドし、関数値の変化に基づく基準を設定
  * `weights`: 重要性に応じて重み付けされたインデックスのベクター。`indexweight`関数によって生成可能
  * `opttimeout`: ユーザーが最適化に対して壁時計タイムアウトを設定できるようにし、失敗した最適化を停止して安全に戻るために使用
  * `optmaxeval`: ユーザーが最適化中の最大評価数を設定できるようにし、再現性が必要な場合に使用
