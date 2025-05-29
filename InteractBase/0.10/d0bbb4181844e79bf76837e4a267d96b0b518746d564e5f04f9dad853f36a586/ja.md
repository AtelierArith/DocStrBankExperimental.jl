`button(content... = "Press me!"; value=0)`

ボタンです。`content`はボタンの中に入ります。ボタンの`content`は特別な`clicks`変数をサポートしており、各クリックごとに`1`ずつ増加します。例えば、`button("clicked {{clicks}} times")`のように使用します。`clicks`変数は`value=0`で初期化されます。ボタン`b`がある場合、`b["is-loading"]`はボタンが読み込み状態（スピニングホイール）にあるかどうかを定義します。スピナーを表示するには`b["is-loading"][]=true`、スピナーを取り除くには`b["is-loading"][]=false`をそれぞれ使用します。
