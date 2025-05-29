  * `save(filename, data...)` は、`filename` からフォーマットを推測し、フォーマットされたファイルの内容を保存します。
  * `save(Stream{format"PNG"}(io), data...)` はフォーマットを直接指定し、フォーマット [`query`](@ref) をバイパスします。
  * `save(File{format"PNG"}(filename), data...)` はフォーマットを直接指定し、フォーマット [`query`](@ref) をバイパスします。
  * `save(f, data...; options...)` はキーワード引数をセーバーに渡します。
