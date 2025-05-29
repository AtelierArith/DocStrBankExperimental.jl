Erlang累積開発プロセス

Erlang開発プロセスは、プロセスの期間を表すために整数の形状パラメータを持つガンマ分布を使用します。

`AccErlang()`は、次のフィールドを持つ構造体を返します：     - `pars`    は、`devmn`と`devsd`を持つNamedTuple引数を取り、`k`、`theta`、および`stay`を計算します（その順序でタプルとして返されます）     - `eval`    は、引数`i`、`k`、および`theta`を取り、`i`で評価された累積密度関数を返します     - `func`    は、引数`heval`、`d`、`q`、`k`、`theta`、および`qkey`を取り、ハザードを返します     - `check`   は、数値引数を取り、プロセスインジケーターが完了閾値（デフォルトは1.0）を超えたかどうかをチェックします     - `stepper`は、StepperTypes引数（例：`AccStepper`、`AgeStepper`、または`CustomStepper`）を取ります。

構造体`AccErlang`は、抽象型`AccHaz`から継承されます（それ自体はスーパタイプ`HazTypes`を持ちます）。
