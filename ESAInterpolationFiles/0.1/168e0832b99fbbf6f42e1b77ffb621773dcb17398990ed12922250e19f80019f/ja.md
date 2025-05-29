```
IPF{C, V}
```

ESA/ESOC補間ファイルデータを格納するための構造体。

  * `filepath::String`: IPFファイルへのパス。
  * `header::IPFHeader`: IPFファイルのヘッダー情報。
  * `blocks::Vector{IPFBlockInfo}`: IPFファイル内のブロックに関する情報。
  * `first_key::V`: IPFファイルに格納されている最初のキー値。
  * `last_key::V`: IPFファイルに格納されている最後のキー値。
  * `array::Vector{UInt8}`: IPFファイルのバイナリデータを含む配列。
  * `cache::InterpCache{C, V}`: 補間データのキャッシュ。

ここでのパラメータはキャッシュタイプ `C` と値タイプ `V` です。

## コンストラクタ

  * `IPF{C, V}(filepath::String)`: 指定されたファイルパスから `IPF` オブジェクトを構築し、キャッシュ (`C`) と値 (`V`) のタイプを指定するオプションがあります。
  * `IPF(filepath::String)`: キャッシュと値の両方にデフォルトタイプ `Float64` を使用して `IPF` オブジェクトを構築します。
