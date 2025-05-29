```
simulate(state, program, tape_left, tape_right)
```

チューリングマシンの1ステップをシミュレートします：読み取り、書き込み、ヘッドの移動。

入力

  * `state`::String : チューリングマシンの現在の状態
  * `program`::Dict{Any,Any} with `m` entries: [states,read*cells]のキーと[next*state,write_cell,movement]の値を持つ辞書
  * `tape_left`::Deque{Int} : ヘッドの左側のスタックの値
  * `tape_right`::Deque{Int} : ヘッドの右側のスタックの値

出力

  * `state`::String : 1回のシミュレーションステップ後のチューリングマシンの更新された状態
  * `tape_left`::Deque{Int} : 1回のシミュレーションステップ後のヘッドの左側のスタックの更新された値
  * `tape_right`::Deque{Int} : 1回のシミュレーションステップ後のヘッドの右側のスタックの更新された値
