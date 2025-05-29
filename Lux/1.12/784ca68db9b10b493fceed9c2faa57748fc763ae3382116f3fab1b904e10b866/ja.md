```
StatefulRecurrentCell(cell)
```

再帰セル（[`RNNCell`](@ref)、[`LSTMCell`](@ref)、[`GRUCell`](@ref)のような）をラップし、状態を持つようにします。

未定義の動作を避けるために、単一のデータシーケンスの処理が完了したら、`Lux.update_state(st, :carry, nothing)`を使用して状態を更新してください。

## 引数

  * `cell`: 再帰セル。再帰セルの入力/出力がどのように構造化されるべきかについては、[`RNNCell`](@ref)、[`LSTMCell`](@ref)、[`GRUCell`](@ref)を参照してください。

## 入力

  * `cell`への入力。

## 戻り値

  * シーケンス全体に対する`cell`の出力。
  * `cell`の状態を更新し、更新された`carry`。

## 状態

  * NamedTupleを含む：

      * `cell`: `cell`と同じ。
      * `carry`: `cell`のキャリーステート。
