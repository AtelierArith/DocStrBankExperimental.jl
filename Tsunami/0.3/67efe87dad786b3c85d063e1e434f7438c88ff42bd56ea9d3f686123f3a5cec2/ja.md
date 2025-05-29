```
Tsunami.log(trainer::Trainer, name::AbstractString, value; 
    [on_step, on_epoch, prog_bar, batchsize])
```

`name`という名前で`value`をログに記録します。トレーニングループ内の任意の関数やコールバックから呼び出すことができます。`trainer.loggers`で指定されたロガーにログを記録します。

詳細については、[Logging](@ref) ドキュメントを参照してください。

`on_step`が`true`の場合、値は各ステップでログに記録されます。`on_epoch`が`true`の場合、値は蓄積され、各エポックでログに記録されます。この場合、デフォルトの集約はバッチの`mean`であり、バッチサイズも考慮されます。`on_step`と`on_epoch`の両方が`true`の場合、値は`"<name>_step"`および`"<name>_epoch"`としてログに記録されます。

# 引数

  * `trainer::Trainer`: トレーナーオブジェクト。
  * `name::AbstractString`: 値の名前。
  * `value`: ログに記録する値。
  * `batchsize`: 現在のバッチのサイズ。`on_epoch == True`のときのみ、バッチを集約するために使用されます。デフォルトは`trainer.fit_state.batchsize`です。
  * `on_epoch::Bool`: 各エポックで値をログに記録するかどうか。`stage`が`:train_epoch_end`または`:val_epoch_end`の場合はデフォルトで`true`、それ以外の場合は`false`です。
  * `on_step::Bool`: 各ステップで値をログに記録するかどうか。`stage`が`:training`の場合はデフォルトで`true`、`:validation`および`:testing`の場合は`false`です。
  * `prog_bar::Bool`: プログレスバーに値をログに記録するかどうか。デフォルトは`true`です。

# 例

```julia
function val_step(model::Model, trainer, batch, batch_idx)
    # 検証損失をログに記録
    ...
    Tsunami.log(trainer, "val/loss", val_loss)
end
```
