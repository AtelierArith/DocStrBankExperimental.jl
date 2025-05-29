```
Checkpointer(model;
             schedule,
             dir = ".",
             prefix = "checkpoint",
             overwrite_existing = false,
             verbose = false,
             cleanup = false,
             properties = default_checkpointed_properties(model))
```

`schedule` に基づいてモデルを JLD2 ファイルにチェックポイントする `Checkpointer` を構築します。`model.clock.iteration` がファイル名に含まれ、複数のチェックポイントファイルを区別します。

チェックポイントからモデルを再起動または「ピックアップ」するには、`run!` を呼び出す際に `pickup = true` を指定し、チェックポイントファイルがディレクトリ `dir` にあることを確認してください。詳細については [`run!`](@ref) を参照してください。

追加のモデル `properties` を指定することができますが、`:timestepper` のような重要なプロパティを削除すると、チェックポイントからの復元が不可能になります。

チェックポインターは、モデルの可能な限り多くをディスクにシリアライズしようとしますが、関数や関数を含むオブジェクトは現時点ではシリアライズできません。

# キーワード引数

  * `schedule` (必須): チェックポイントを取得するタイミングを決定するスケジュール。
  * `dir`: 出力を保存するディレクトリ。デフォルト: `"."` (現在の作業ディレクトリ)。
  * `prefix`: すべての出力ファイルに接頭辞として付けられる説明的なファイル名。デフォルト: `"checkpoint"`。
  * `overwrite_existing`: ファイル名が衝突する場合、既存のファイルを削除します。デフォルト: `false`。
  * `verbose`: 出力ライターが行っていることを、計算/書き込み時間やファイルサイズの統計と共にログに記録します。デフォルト: `false`。
  * `cleanup`: 新しいチェックポイントファイルが書き込まれると、以前のチェックポイントファイルが削除されます。デフォルト: `false`。
  * `properties`: チェックポイントするモデルのプロパティのリスト。このリストには必ず `:grid`、`:particles`、および `:clock` が含まれている必要があり、AB2 タイムステッピングを使用する場合は `:timestepper` も含める必要があります。デフォルト: `model` に対して [`default_checkpointed_properties`](@ref) を呼び出してこれらのプロパティを取得します。
