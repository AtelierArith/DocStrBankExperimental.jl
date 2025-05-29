ダミー年齢依存開発プロセス

これは年齢依存のダミープロセスを実装します。

`AgeDummy()` は、次のフィールドを持つ構造体を返します：

  * `pars`    は、`devmn` と `devsd` を持つ NamedTuple 引数を取り、`k`、`theta`、および `stay` を計算します（その順序でタプルとして返されます）
  * `eval`    は、引数 `i`、`k`、および `theta` を取り、`i` で評価された累積密度関数を返します
  * `func`    は、引数 `heval`、`d`、`q`、`k`、`theta`、および `qkey` を取り、ハザードを返します
  * `check`   は、数値引数を取り、プロセスインジケーターが完了閾値を超えたかどうかをチェックします（デフォルトは 1.0）
  * `stepper` は、StepperTypes 引数を取り（例：`AccStepper`、`AgeStepper`、または `CustomStepper`）。

構造体 `AgeDummy` は、抽象型 `CusHaz` から継承されます（それ自体はスーパタイプ `HazTypes` を持ちます）。
