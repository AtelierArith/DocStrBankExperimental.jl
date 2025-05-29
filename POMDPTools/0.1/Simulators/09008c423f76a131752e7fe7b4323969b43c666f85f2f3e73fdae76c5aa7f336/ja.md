後で検査するための履歴を記録するシミュレーター

シミュレーションは、次のいずれかが発生したときに終了します。

1. 終端状態に達したとき（`isterminal()`によって判断される）または
2. 割引率が`eps`と同じくらい小さいとき、または
3. max_stepsが実行されたとき

キーワード引数:     - `rng`: シミュレーションのための乱数生成器     - `capture_exception::Bool`: 例外をキャッチして履歴に保存するか、未処理のままにしてスクリプトを終了させるか     - `show_progress::Bool`: シミュレーションの進行状況を示すプログレスバーを表示するか     - `eps`     - `max_steps`

使用法（オプション引数は角括弧内に）:

```
hr = HistoryRecorder()
history = simulate(hr, pomdp, policy, [updater [, init_belief [, init_state]]])
```
