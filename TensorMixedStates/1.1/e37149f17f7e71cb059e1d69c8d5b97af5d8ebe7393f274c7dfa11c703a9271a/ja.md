```
struct State
State(Pure()|Mixed(), ::System, states)
State(Pure()|Mixed(), ::Int, ::AbstractSite, state)
State(Pure()|Mixed(), ::Vector{<:AbstractSite}, state)
State(::State, ::MPS)
```

シミュレーションされた量子システムの完全な状態を表します

# フィールド

  * `type::Union{Pure, Mixed}`: ピュアまたはミックスの表現
  * `system::System`: システムの説明
  * `state::MPS`: システムの状態
  * `preobs::PreObs`: 演算子を計算するための前処理データ

# 例

```
State(Pure(), system, "Up")
State(Mixed(), system, ["Up", "Dn", "Up"])
State(Mixed(), system, "FullyMixed")
State(Pure(), system, [1, 0])
State(Pure(), 10, Qubit(), "Up")
State(Mixed(), [Qubit(), Boson(4), Fermion()], ["Up", "2", "Occ"])
State(state, mps)        returns a new state with the same system but a new mps
```

# 操作

状態は加算、減算、数値との乗算が可能です
