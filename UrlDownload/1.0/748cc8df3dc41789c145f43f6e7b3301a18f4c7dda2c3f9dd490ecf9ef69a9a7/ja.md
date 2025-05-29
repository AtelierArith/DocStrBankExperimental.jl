```
urldownload(url, progress = false;
            parser = nothing, format = nothing, save_raw = nothing,
            compress = :auto, multifiles = false, headers = HTTP.Header[],
            httpkw = Pair[], update_period = 1, kw...)
```

対応する `url` からファイルをメモリにダウンロードし、必要なデータ構造に処理します。

# 引数

  * `url`: ダウンロードのためのURL
  * `progress`: `ProgressMeter` を表示します。デフォルトでは表示されません。
  * `parser`: カスタムパーサー。1つの位置引数 `Vector{UInt8}` とオプションのキーワード引数を受け取り、必要なデータ構造を返す関数です。パーサーが設定されている場合、`format` などの他の設定を上書きします。パーサーが設定されていない場合、内部パーサーがデータ処理に使用されます。
  * `format`: 固定フォーマットの1つ (:CSV, :PIC, :FEATHER, :JSON)。設定されている場合、自動検出メカニズムを上書きします。
  * `save_raw`: `String` または `IO` に設定されている場合、ダウンロードされた生データが対応するストリームに保存されます。
  * `compress`: デフォルトは :auto で、:none, :xz, :gzip, :bzip2, :lz4, :zstd, :zip のいずれかです。ファイルが圧縮されているかどうかと圧縮タイプを決定します。解凍されたデータはカスタム `parser` または内部パーサーによって処理されます。デフォルトでは、`:zip` 以外の圧縮タイプの場合、内部パーサーは `CSV.File` であり、`:zip` の場合は通常のルールが適用されます。`compress` が `:none` の場合、カスタムパーサーはデータを自分で解凍する必要があります。
  * `multifiles`: デフォルトは `false` で、`:zip` 圧縮データの場合、アーカイブ内の最初のファイルのみを処理するか、解凍され処理されたオブジェクトの配列を返すかを定義します。
  * `headers`: リクエストのHTTPヘッダーを設定する `HTTP.jl` の引数。
  * `httpkw`: `GET` 関数に渡される `HTTP.jl` の追加キーワード引数。ペアのベクターとして提供する必要があります。
  * `update_period`: `ProgressMeter` の更新期間。デフォルトは1秒です。
  * `kw...`: データパーサーに渡すべき任意のキーワード引数。
