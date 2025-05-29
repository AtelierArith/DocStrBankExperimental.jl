```
eval_R!(res::AbstractArray{Float64,1}, point::AbstractArray{Float64, 2}, ::MED) where MED <: AbstractModelEvaluationData
```

与えられた点でモデルの残差を評価し、指定されたモデル評価構造を使用します。残差は提供されたベクターに格納されます。

### 実装の詳細 (開発者向け)

新しいタイプのモデル評価データを作成する際には、この関数のメソッドをそのタイプに特化させて定義する必要があります。

`point` 引数は2次元配列で、行数は `maxlag+maxlead+1` に等しく、列数はモデルの `variables+shocks+auxvars` の数に等しくなります。`res` ベクターは方程式の数 + 補助方程式の長さと同じになります。あなたの実装は `point` を変更せず、`res` を更新する必要があります。

参照: [`eval_RJ`](@ref)
