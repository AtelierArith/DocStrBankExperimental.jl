Avro.jlパッケージは、[avroフォーマット](http://avro.apache.org/docs/current/spec.html)でデータを読み書きするための純粋なJulia実装を提供します。

### 実装状況

現在サポートされているもの：

  * すべてのプリミティブ型
  * すべてのネストされた/複雑な型
  * スペックに記載されている論理型（Decimal、UUID、Date、Time、Timestamps、Duration）
  * バイナリエンコーディング/デコーディング
  * Tables.jlインターフェースを介したオブジェクトコンテナファイルの読み書き
  * オブジェクトコンテナファイルのためのxz、zstd、deflate、bzip2圧縮コーデックをサポート

現在サポートされていないもの：

  * オブジェクトのJSONエンコーディング/デコーディング
  * 単一オブジェクトのエンコーディングまたはスキーマフィンガープリント
  * スキーマ解決
  * プロトコルメッセージ、呼び出し、ハンドシェイク
  * Snappy圧縮

### パッケージの動機

他のデータフォーマットに対してavroフォーマットを使用する理由は何ですか？いくつかの利点は次のとおりです：

  * 非常に簡潔なバイナリエンコーディング、特に圧縮されたオブジェクトコンテナファイル
  * 非常に高速な読み書き
  * オブジェクト/データは明確に定義されたスキーマを持つ必要がある
  * 数少ない「行指向」のバイナリデータフォーマットの1つ

### 始めに

Avro.jlパッケージは、avroデータと対話するための2つの主要なAPIをサポートしています。最初のものは、jsonデータと対話するためのJSON3.jl構造体APIに似ており、主にavroフォーマットとjsonの類似性によるものです。これは次のようになります：

```julia
buf = Avro.write(obj)
obj = Avro.read(buf, typeof(obj))
```

要するに、[`Avro.write`](@ref)を使用し、avroフォーマットで書き出すオブジェクト`obj`を提供します。データを書き込むために、オプションでファイル名または`IO`を最初の引数として提供できます。

次に、[`Avro.read`](@ref)を使用してデータを読み戻すことができ、最初の引数はファイル名、`IO`、またはavroデータを含む任意の`AbstractVector{UInt8}`バイトバッファでなければなりません。2番目の引数は*必須*で、読み取るデータの型です。この型は、単純なJulia型（例えば`Avro.read(buf, Vector{String})`）として提供することも、`Avro.read(buf, Avro.parseschema("schema.avsc"))`のように解析されたavroスキーマとして提供することもできます。[`Avro.parseschema`](@ref)は、読み取るデータのavroスキーマを表すファイル名またはjson文字列を受け取り、`Avro.read`に渡すことができる「スキーマ型」を返します。

2番目の代替APIは、avro仕様が「オブジェクトコンテナ」と呼ぶファイル内でデータのスキーマをデータと「パッケージ化」することを可能にします。`Avro.read`/`Avro.write`は、ユーザーがすでにスキーマを知っているか、外部からスキーマを渡す必要がありますが、[`Avro.writetable`](@ref)と[`Avro.readtable`](@ref)はavroオブジェクトコンテナファイルを読み書きでき、スキーマの書き込み/読み取り、圧縮などを自動的に処理します。これらのテーブル関数は、他のフォーマットとの統合を容易にするために、当然ながら普遍的なTables.jlインターフェースを利用しています。

```julia
# zstd圧縮コーデックを使用して、"data.avro"という名前のファイルにinput_tableを書き出します
# input_tableはCSV.File、Arrow.Table、DataFrameなど、任意のTables.jl互換ソースである可能性があります。
Avro.writetable("data.avro", input_table; compress=:zstd)

# オブジェクトコンテナファイルからavroデータを読み取ることもできます
# ファイルが圧縮を使用している場合、自動的に解凍されます
# データのスキーマはオブジェクトコンテナファイル自体にパッケージ化されており
# ファイルテーブルを構築する前に解析されます
tbl = Avro.readtable("data.avro")
# 戻り値の型は`Avro.Table`で、Tables.jlインターフェースを満たします
# これは、Arrow.write("data.arrow", tbl)、CSV.write("data.csv", tbl)、またはDataFrame(tbl)のような
# 有効なシンク関数に送信できることを意味します
```
