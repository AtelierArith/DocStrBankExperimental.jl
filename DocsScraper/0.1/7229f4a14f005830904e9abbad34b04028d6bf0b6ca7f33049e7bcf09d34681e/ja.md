```
make_knowledge_packs(crawlable_urls::Vector{<:AbstractString} = String[];
    single_urls::Vector{<:AbstractString} = String[],
    max_chunk_size::Int = MAX_CHUNK_SIZE, min_chunk_size::Int = MIN_CHUNK_SIZE,
    model_embedding::AbstractString = MODEL_EMBEDDING, embedding_dimension::Int = EMBEDDING_DIMENSION, custom_metadata::AbstractString = "",
    embedding_bool::Bool = EMBEDDING_BOOL, index_name::AbstractString = "",
    target_path::AbstractString = "", save_url_map::Bool = true)
```

クローリング、パース、および埋め込みを生成するためのエントリーポイント。作成されたインデックスの tar.gz ファイルへのパスを返します。注意: `index_name` を渡すことをお勧めします。これが生成されるインデックスの名前になります。

# 引数

  * crawlable_urls: さらにリンクを見つけるためにクローリングされるべき URL
  * single_urls: 単一ページの URL で、単にスクレイピングおよびパースされるべきもの。クローラーはさらに URL を探しません
  * max*chunk*size: 最大チャンクサイズ
  * min*chunk*size: 最小チャンクサイズ
  * model_embedding: 埋め込みモデル
  * embedding_dimension: 埋め込み次元
  * custom_metadata: 必要に応じてエコシステム名などのカスタムメタデータ
  * embedding_bool: true の場合、生成される埋め込みはブール値、そうでない場合は Float32
  * index_name: インデックスの名前。デフォルト: gensym によって生成された "index" シンボル
  * target_path: インデックスフォルダが作成されるディレクトリへのパス
  * save*url*map: true の場合、クローリングされた URL とそれに関連するパッケージ名の CSV を作成します
