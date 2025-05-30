```
GPModel <: JuMP.AbstractModel
```

幾何プログラミング問題のためのモデルタイプです。これは、幾何プログラミングの制約と変換を処理するためにJuMPのモデル機能を拡張します。

幾何プログラムには以下が含まれます：

  * ポリソノミアルの最小化またはモノミアルの最大化
  * モノミアル等式制約（= 1）に従う
  * およびポリソノミアル不等式制約（≤ 1）

# 例

```julia
using GSOpt

# 幾何プログラミングモデルを作成
model = GPModel()

# 変数を追加（幾何プログラミングでは正でなければならない）
@variable(model, x >= 1)
@variable(model, y >= 1)

# 目的を設定（ポリソノミアルを最小化）
@objective(model, Min, 2x + 3y + 4x*y)

# 制約を追加
@constraint(model, x*y <= 10)  # ポリソノミアル不等式
@constraint(model, x*y^2 == 20)  # モノミアル等式

# モデルを解く
optimize!(model)

# 結果を取得
value(x)
value(y)
objective_value(model)
```
