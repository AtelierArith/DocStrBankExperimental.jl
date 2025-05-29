```
scparams([T], X::AbstractSparseMatrix, features;
         method=:poisson,
         min_cells::Integer=5,
         feature_type,
         feature_mask,
         feature_names,
         use_cache=true,
         cache_read=use_cache,
         cache_write=use_cache,
         verbose=true,
         chunk_size=100,
         nthreads=Threads.nthreads(),
         channel_size=nthreads*4)
```

カウント行列 `X` から SCTransform パラメータ推定を計算します。`features` は行として特徴、列として細胞を持つテーブル（例：DataFrame または NamedTuple）である必要があります。`T` は出力パラメータテーブルの型のためのオプションのパラメータです。デフォルトでは `features` と同じ型になります。デフォルトでは、結果は `Scratch.jl` を使用してスクラッチスペースにキャッシュされ、Julia セッション間での不必要な再計算を避けます。

一般:

  * `method` - パラメータ推定のアルゴリズムを決定します。`：poisson` または `：nb`（負の二項分布）のいずれかです。最初に `poisson` 推定を行い、その後に分散を推定する `：poisson` を推奨します。
  * `feature_names` - 各特徴の名前を持つベクター。`@warn` メッセージにのみ使用されます。デフォルトでは `features` の `name` 列、または名前が存在しない場合は `id` 列になります。
  * `verbose` - true の場合、進行状況バーとその他の情報が表示されます。

特徴選択:

  * `min_cells` - 非ゼロカウントが少なくとも `min_cells` の細胞に存在する特徴のみが含まれます。
  * `feature_type` - `feature_mask` のデフォルトに使用される便利なパラメータ。`features` に `feature_type` 列がある場合は "Gene Expression" がデフォルトになります。
  * `feature_mask` - どの特徴を使用するかを決定するブール値のベクター。明示的に設定されている場合、`feature_type` パラメータは無視され、それ以外の場合は `feature_mask` は指定された `feature_type` のみを選択することがデフォルトになります。

キャッシュ:

  * `use_cache` - キャッシュの有効/無効を設定します。
  * `cache_read` - キャッシュの読み取りのみを有効/無効にするためのより細かい制御。
  * `cache_write` - キャッシュの書き込みのみを有効/無効にするためのより細かい制御。

スレッドの詳細:

  * `chunk_size` - 1 チャンクで処理する特徴の数。
  * `nthreads` - パラメータ推定に使用するスレッドの数。
  * `channel_size` - キューに保持するチャンクの数。

# 例

SCTransform パラメータ推定を計算します（遺伝子発現特徴）:

```
julia> scparams(X, features)
```

SCTransform パラメータ推定を計算します（抗体キャプチャ特徴）:

```
julia> scparams(X, features; feature_type="Antibody Capture")
```

参照: [`sctransform`](@ref)
