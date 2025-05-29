```
set_up(init_state, input)
```

シングルテープのシミュレーションの初期セットアップを行います。`length(input)`は1以上でなければなりません。入力はヘッドの右側のテープに配置されます。

入力

  * `input`::`n`-要素 Array{Char, 1} : ヘッドの右側に挿入する初期データ
  * `init_state`::String : チューリングマシンの初期/開始状態の文字列ラベル

出力

  * `tape_left`::Deque{Int} : ヘッドの左側のスタックの初期値
  * `tape_right`::Deque{Int} : ヘッドの右側のスタックの初期値
