いくつかのパッケージは、ファイルの内容を一度にすべてではなく、チャンクで書き込むストリーミングAPIを実装している場合があります。これらの高レベルのストリームは、画像やビデオまたはオーディオのチャンクのようなフォーマットされたオブジェクトを受け入れるべきです。

  * `savestreaming(filename, data...)` は、`filename` からフォーマットを推測しようとしながら、フォーマットされたファイルの内容を保存します。
  * `savestreaming(File{format"WAV"}(filename))` は、フォーマットを直接指定し、フォーマット [`query`](@ref) をバイパスします。
  * `savestreaming(Stream{format"WAV"}(io))` は、フォーマットを直接指定し、フォーマット [`query`](@ref) をバイパスします。
  * `savestreaming(f, data...; options...)` は、キーワード引数をセーバーに渡します。
