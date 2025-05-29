シミュレーション状態を作成するためのフェーズタイプ

# フィールド

  * `name`: フェーズの名前
  * `time_start`: 初期シミュレーション時間
  * `final_measures`: フェーズの終了時に行う測定（`measure`および`output`を参照）
  * `type`: 作成する状態のタイプ `Pure()` または `Mixed()`
  * `system`: システムを説明するためのSystemオブジェクト（`System`を参照）（Stateオブジェクトが与えられた場合は未使用）
  * `state`: 状態の説明（またはStateオブジェクト）
  * `randomize`: 作成するランダム状態のリンク次元（デフォルトはランダム化なしの0）

# 例

```
CreateState(type = Pure(), system = System(10, Qubit()), state = "Up")
CreateState(type = Mixed(), system = System(3, Qubit()), state = ["Up", "Dn", "Up])
CreateState(type = Pure(), system = System(10, Qubit()), randomize = 50)
CreateState(type = Pure(), system = System(10, Qubit()), state = "Up", randomize = 50)
CreateState(Pure(), 10, Qubit(), "Up")                                      # シンプルな形式
CreateState(Mixed(), [Qubit(), Boson(4), Fermion()], ["Up", "2", "Occ"])    # 別のシンプルな形式
```
