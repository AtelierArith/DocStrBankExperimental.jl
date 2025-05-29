固定期間年齢依存開発プロセス

この年齢依存開発プロセスは、累積密度関数として`devmn`で不連続なステップ関数を使用します。

`AgeFixed()`は、次のフィールドを持つ構造体を返します：     - `pars`    `devmn`と`devsd`を持つNamedTuple引数を取り、`k`、`theta`、および`stay`を計算します（その順序でタプルとして返されます）     - `eval`    引数`i`、`k`、および`theta`を取り、`i`で評価された累積密度関数を返します     - `func`    引数`heval`、`d`、`q`、`k`、`theta`、および`qkey`を取り、ハザードを返します     - `check`   数値引数を取り、プロセスインジケーターが完了閾値（デフォルトは1.0）を超えたかどうかをチェックします     - `stepper` ステッパータイプ引数（例：`AccStepper`、`AgeStepper`、または`CustomStepper`）を取ります。

構造体`AgeFixed`は、抽象型`AgeHaz`から継承されます（それ自体はスーパタイプ`HazTypes`を持ちます）。
