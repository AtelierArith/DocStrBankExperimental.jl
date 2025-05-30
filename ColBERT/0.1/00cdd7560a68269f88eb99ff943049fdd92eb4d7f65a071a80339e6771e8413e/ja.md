```
ColBERTConfig(; use_gpu::Bool, rank::Int, nranks::Int, query_token_id::String,
        doc_token_id::String, query_token::String, doc_token::String, checkpoint::String,
        collection::String, dim::Int, doc_maxlen::Int, mask_punctuation::Bool,
        query_maxlen::Int, attend_to_mask_tokens::Bool, index_path::String,
        index_bsize::Int, nbits::Int, kmeans_niters::Int, nprobe::Int, ncandidates::Int)
```

さまざまなコンポーネントの実行とトレーニングのための設定を含む構造体。

# 引数

  * `use_gpu`: GPUを使用するかどうか。デフォルトは`false`。
  * `rank`: 実行中のGPUのインデックス。デフォルトは`0`。現時点では、このパッケージはこれを`0`のみに制限しています。
  * `nranks`: 実行に使用されるGPUの数。デフォルトは`1`。現時点では、このパッケージは1つのGPUのみをサポートしています。
  * `query_token_id`: クエリトークンの一意の識別子（デフォルトは`[unused0]`）。
  * `doc_token_id`: ドキュメントトークンの一意の識別子（デフォルトは`[unused1]`）。
  * `query_token`: クエリトークンを表すために使用されるトークン（デフォルトは`[Q]`）。
  * `doc_token`: ドキュメントトークンを表すために使用されるトークン（デフォルトは`[D]`）。
  * `checkpoint`: 基本となるColBERTモデルのHuggingFaceチェックポイントへのパス。デフォルトは`"colbert-ir/colbertv2.0"`。
  * `collection`: ドキュメントを含むファイルへのパス。デフォルトは`""`。
  * `dim`: ドキュメント埋め込み空間の次元。デフォルトは128。
  * `doc_maxlen`: ドキュメントがフィットするようにトリミングされる前の最大長。デフォルトは220。
  * `mask_punctuation`: ドキュメント内の句読点文字トークンをマスクするかどうか。デフォルトはtrue。
  * `query_maxlen`: トリミングされる前のクエリの最大長。
  * `attend_to_mask_tokens`: クエリ内のマスクトークンに注意を払うかどうか。デフォルト値はfalse。
  * `index_path`: インデックスファイルを保存するためのパス。
  * `index_bsize`: インデックスの一部で使用されるバッチサイズ。
  * `chunksize`: チャンクのカスタムサイズ、すなわち、1つのチャンクに保存されるデータのパッセージ数。デフォルトは`missing`で、この場合`chunksize`は`collection`と`nranks`のサイズから決定されます。
  * `passages_batch_size`: エンコーディング関数にバッチとして送信されるパッセージの数。デフォルトは`300`。
  * `nbits`: 残差を圧縮するために使用されるビット数。
  * `kmeans_niters`: k-meansクラスタリングに使用される反復回数。
  * `nprobe`: 検索中に取得する最近傍セントロイドの数。デフォルトは`2`。`retrieve`も参照してください。
  * `ncandidates`: 検索中の候補生成で取得する候補の数。デフォルトは`8192`。`retrieve`も参照してください。

# 戻り値

[`ColBERTConfig`](@ref)オブジェクト。

# 例

ほとんどのユーザーは、ほとんどの設定でデフォルトを使用したいと思うでしょう。最小限の例を示します：

```julia-repl
julia> using ColBERT;

julia> config = ColBERTConfig(
           use_gpu = true,
           collection = "/home/codetalker7/documents",
           index_path = "./local_index"
       );
```
