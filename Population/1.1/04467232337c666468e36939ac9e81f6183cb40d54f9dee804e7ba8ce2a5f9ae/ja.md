ネガティブバイノミアル年齢依存開発プロセス

この年齢依存開発プロセスの期間は、ネガティブバイノミアル分布に従います。

`AgeNbinom()` は、次のフィールドを持つ構造体を返します：     - `pars`    `devmn` と `devsd` を持つ NamedTuple 引数を取り、`k`、`theta`、および `stay` を計算します（その順序でタプルとして返されます）     - `eval`    引数 `i`、`k`、および `theta` を取り、`i` で評価された累積密度関数を返します     - `func`    引数 `heval`、`d`、`q`、`k`、`theta`、および `qkey` を取り、ハザードを返します     - `check`   数値引数を取り、プロセス指標が完了閾値（デフォルトは 1.0）を超えたかどうかをチェックします     - `stepper` ステッパータイプの引数を取り（例：`AccStepper`、`AgeStepper`、または `CustomStepper`）。

構造体 `AgeNbinom` は、抽象型 `AgeHaz` から継承されます（それ自体はスーパタイプ `HazTypes` を持ちます）。
