```julia
mutable struct ContState{Tv, T, Teigvals, Teigvec, Tcb} <: BifurcationKit.AbstractContinuationState{Tv}
```

継続手続きの状態を含む可変構造体。フィールドは継続手続き中に変更されることを意図しています。

!!! danger
    これらのフィールドを自分で変更すると、継続手続きが壊れる可能性があります。フィールドにアクセスするには、以下のメソッドを使用してください。これらはコピーを生成しません。


# 引数

  * `z_pred` ブランチ上の現在の解
  * `converged` ニュートン補正のためのブール値
  * `τ` 接線予測子
  * `z` 前の解
  * `itnewton` ニュートン反復の回数（補正器内）
  * `step` 現在の継続ステップ
  * `ds` ステップサイズ
  * `stopcontinuation` 継続を停止するためのブール値

# 有用な関数

  * `copy(state)` `state`のコピーを返します
  * `copyto!(dest, state)` `state`を`dest`にコピーします
  * `getsolution(state)` 現在の解 (x, p) を返します
  * `gettangent(state)` 現在の解での接線を返します
  * `getpredictor(state)` 現在の解での予測子を返します
  * `getx(state)` 現在の解のx成分を返します
  * `getp(state)` 現在の解のp成分を返します
  * `get_previous_solution(state)` 前の解 (x, p) を返します
  * `getpreviousx(state)` 前の解のx成分を返します
  * `getpreviousp(state)` 前の解のp成分を返します
  * `is_stable(state)` 現在の状態が安定かどうかを返します
