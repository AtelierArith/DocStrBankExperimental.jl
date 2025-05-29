ガンマ年齢依存開発プロセス

この年齢依存開発プロセスはガンマ分布に従います。

`AgeGamma()` は次のフィールドを持つ構造体を返します:     - `pars`    は `devmn` と `devsd` を持つ NamedTuple 引数を取り、`k`、`theta`、および `stay` を計算します（その順序でタプルとして返されます）     - `eval`    は引数 `i`、`k`、および `theta` を取り、`i` で評価された累積密度関数を返します     - `func`    は引数 `heval`、`d`、`q`、`k`、`theta`、および `qkey` を取り、ハザードを返します     - `check`   は数値引数を取り、プロセス指標が完了閾値（デフォルトは 1.0）を超えたかどうかをチェックします     - `stepper` は StepperTypes 引数（例: `AccStepper`、`AgeStepper`、または `CustomStepper`）を取ります。

構造体 `AgeGamma` は抽象型 `AgeHaz` から継承されます（それ自体はスーパタイプ `HazTypes` を持ちます）。
