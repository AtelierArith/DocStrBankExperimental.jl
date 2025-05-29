RollingLogger(filename, sizelimit, nfiles, min*level=Info; timestamp*identifier::Symbol=:time, format::Symbol=:console) ログファイルにログを記録します。ファイルサイズに基づいてログファイルをローテーションします。ローテーションされたログを圧縮します。

ログは、オプションのキーワード引数 `format` を `:json` に設定することでJSON形式にフォーマットできます。JSON形式のログエントリはJSONオブジェクトです。以下のキーを持つべきです（空でない限り）：メッセージ部分には、以下のキーを含めることができます（空でない限り）：

  * `metadata`: イベントメタデータ（例：タイムスタンプ、行、ファイル名、...）
  * `message`: ログメッセージ文字列
  * `keywords`: 提供されたキーワード
