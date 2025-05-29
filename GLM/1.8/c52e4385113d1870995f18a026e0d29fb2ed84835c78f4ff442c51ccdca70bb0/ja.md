```
fit(LinearModel, formula, data, allowrankdeficient=false;
   [wts::AbstractVector], dropcollinear::Bool=true)
fit(LinearModel, X::AbstractMatrix, y::AbstractVector;
    wts::AbstractVector=similar(y, 0), dropcollinear::Bool=true)
```

データに線形モデルをフィットします。

最初のメソッドでは、`formula` は [StatsModels.jl `Formula` オブジェクト](https://juliastats.org/StatsModels.jl/stable/formula/) でなければならず、`data` はテーブル（[Tables.jl](https://tables.juliadata.org/stable/) 定義、例えばデータフレーム）でなければなりません。2番目のメソッドでは、`X` は独立変数の値を列に持つ行列でなければならず（必要に応じて切片を含む）、`y` は従属変数の値を持つベクトルでなければなりません。

キーワード引数 `wts` は観測値の頻度重みを指定する `Vector` であることができます。このような重みは、各観測値をその重みと等しい回数だけ繰り返すことに相当します。この解釈は、等しい点推定を与えますが、他のソフトウェアでのデフォルトである解析的（逆分散）重みや確率（サンプリング）重みとは異なる標準誤差を与えることに注意してください。

`dropcollinear` は、`lm` がフルランク未満のモデル行列を受け入れるかどうかを制御します。`true`（デフォルト）の場合、線形依存列の各セットの最初の列のみが使用されます。冗長な線形依存列の係数は `0.0` であり、関連するすべての統計は `NaN` に設定されます。
