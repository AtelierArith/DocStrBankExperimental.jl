```julia
designmatrix(
    unfoldmodeltype,
    f,
    tbl,
    basisfunction;
    contrasts,
    eventname,
    kwargs...
)

```

designmatrix(type, f, tbl; kwargs...) モデルをフィットさせるために使用される *DesignMatrix* を返します。

# 引数

  * type::UnfoldModel
  * f::FormulaTerm: この designmatrix で使用される式
  * tbl: モデル化されるイベント（通常はデータフレーム）
  * basisfunction::BasisFunction: モデリングに使用される基底関数（指定されている場合）
  * contrasts::Dict: （オプション）式に適用されるコントラスト
  * eventfields::Array: （オプション）基底関数にイベントごとに渡されるシンボルの配列。

配列の最初のフィールドは常にサンプル内のイベント開始を定義します。デフォルトは [:latency]

# 例

```julia-repl
julia>  designmatrix(UnfoldLinearModelContinuousTime,Dict(Any=>(f,basisfunction1),tbl)
```
