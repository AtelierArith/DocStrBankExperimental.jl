```
JsonLogger(; <キーワード引数>)
```

JsonLogger コンストラクタは、通常の `@info`、`@debug` コマンドで使用できる JSON 出力のカスタムロガーを作成します。サポートされているキーワード引数には以下が含まれます：

  * `io` (デフォルト `stdout`): `errlevel` レベル以下のログメッセージを出力するために使用される IO ストリーム。`IO` または `String` のいずれかであり、後者の場合は出力ファイルの名前として扱われます。
  * `ioerr` (デフォルト `stderr`): `errlevel` レベル以上のログメッセージを出力するために使用される IO ストリーム。`IO` または `String` のいずれかであり、後者の場合は出力ファイルの名前として扱われます。
  * `errlevel` (デフォルト `Error`): ログメッセージに使用する出力 IO を決定します。すべてのメッセージを `io` に送信したい場合は、このパラメータを `MiniLoggers.AboveMaxLevel` に設定します。すべてのメッセージを `ioerr` に送信したい場合は、このパラメータを `MiniLoggers.BelowMinLevel` に設定します。
  * `minlevel` (デフォルト: `Info`): このレベル以下のメッセージは無視されます。たとえば、デフォルト設定では `@debug "foo"` は無視されます。
  * `append` (デフォルト: `false`): 出力ストリームに追加するか、最初にファイルを切り詰めるかを定義します。`io` または `ioerr` がファイルパスの場合にのみ使用されます。
  * `flush` (デフォルト: `true`): 各ログメッセージのために IO ストリームを `flush` するかどうか。フラッシュの動作は `flush_threshold` 引数にも影響されます。
  * `squash_delimiter`: (デフォルト: "\t"): マルチラインメッセージを圧縮する際に使用する区切り文字を定義します。
  * `flush_threshold::Union{Integer, TimePeriod}` (デフォルト: 0): この引数がゼロでなく、`flush` が `true` の場合、`io` は `flush_threshold` ミリ秒ごとに一度だけフラッシュされます。つまり、2つの連続したログメッセージの間の時間が `flush_threshold` より短い場合、2つ目のメッセージはフラッシュされず、次のログイベントを待つ必要があります。
  * `dtformat` (デフォルト: "yyyy-mm-dd HH:MM:SS"): `format` 引数で `datetime` パラメータが使用される場合、この日付形式が出力タイムスタンプに適用されます。
  * `levelname` (デフォルト `string`): ログレベル名の出力を再定義することを許可します。形式は `levelname(level::LogLevel)::String` の関数である必要があります。
  * `format`: 出力に使用するキーワードを定義します。定義されている場合、出力 JSON の構造を定義する文字列である必要があります。キーワードを使用し、許可されているキーワードは以下の通りです：

      * `timestamp`: ログメッセージのタイムスタンプ
      * `level`: ログレベルの名前 (Debug, Info など)
      * `filepath`: ログメッセージを生成したファイルのファイルパス
      * `basename`: ログメッセージを生成したファイルのファイルパスのベース名
      * `line`: ログメッセージを生成したファイル内のログコマンドの行番号
      * `group`: ロググループ
      * `module`: ログコマンドを含むモジュールの名前
      * `id`: ログメッセージ ID
      * `message`: メッセージ自体

フォーマット文字列はカンマ区切りのトークンで構成されるべきです。最も単純な形では、トークンは単にキーワードであり、キーワードの名前がフィールド名として使用されます。たとえば、`"timestamp,level,message"` は `{"timestamp":"2023-01-01 12:34:56","level":"Debug","message":"some logging message"}` になります。フィールド名を変更する必要がある場合は、`<field name>:<keyword>` 形式を使用する必要があります。たとえば、`"severity:level"` は `{"severity":"Debug"}` になり、ここでフィールド名は `severity` で、値はログの `level` から取得されます。また、ネストされた JSON を作成することもできます。そのためには、`<field name>:{<format string>}` 形式を使用する必要があり、フォーマット文字列に対する前のルールも適用されます。たとえば、`source:{line, file:basename}` は `{"source":{"line":123,"file":"calculations.jl"}}` になります。

デフォルトでは、`format` は `timestamp,level,basename,line,message` です。
