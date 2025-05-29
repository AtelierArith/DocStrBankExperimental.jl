```
batch_geocode(
    geocoder::Geocoder,
    input::Union{AbstractString, IO},
    output::Union{AbstractString, IO};
    workers::Int = 4,
    retries::Int = 5,
    timeout::Float64 = 60.0,
    input_columns::Union{Vector{Int}, Nothing} = nothing,
    add_columns::Vector{<:AbstractString} = ["formatted", "geometry.lat", "geometry.lng", "confidence", "components._type", "status_message"],
    on_error::Symbol = :log,
    ordered::Bool = false,
    progress::Bool = true,
    limit::Union{Int, Nothing} = nothing,
    optional_api_params::Dict{Symbol, Any} = Dict{Symbol, Any}(),
    rate_limit_semaphore::Union{Base.Semaphore, Nothing} = nothing,
    command::Union{Symbol, Nothing} = nothing
)

CSVファイルまたはIOストリームからのジオコーディングリクエストのバッチを処理します。

この関数は、複数のワーカータスクを使用してジオコーディング操作を同時に実行することにより、大規模なデータセットを効率的に処理します。入力CSVから読み込み、各行をジオコーディングし、結果を出力CSVに書き込みます。

# 引数

  * `geocoder::Geocoder`: リクエストに使用するジオコーダーインスタンス
  * `input::Union{AbstractString, IO}`: 入力CSVファイルのパスまたはIOストリーム
  * `output::Union{AbstractString, IO}`: 出力CSVファイルのパスまたはIOストリーム

# オプションのパラメータ

  * `workers::Int = 4`: 同時に実行するワーカータスクの数
  * `retries::Int = 5`: 失敗したリクエストの再試行回数
  * `timeout::Float64 = 60.0`: リクエストのタイムアウト（秒）
  * `input_columns::Union{Vector{Int}, Nothing} = nothing`: ジオコーディングに使用する特定の列（1ベースのインデックス）

      * `nothing`の場合、すべての列がクエリを形成するために使用されます
      * 単一の列が指定された場合、それは前方ジオコーディングの住所として使用されます
      * 2つの列が指定された場合、それらは逆ジオコーディングの緯度と経度として使用されます
  * `add_columns::Vector{<:AbstractString} = ["formatted", "geometry.lat", "geometry.lng", "confidence", "components._type", "status_message"]`: 出力列として追加するジオコーディング結果のフィールド
  * `on_error::Symbol = :log`: 処理中のエラーの扱い方

      * `:log`: エラーをログに記録し、処理を続行します（デフォルト）
      * `:skip`: エラーのある行をスキップします
      * `:fail`: いずれかのエラーで処理を停止します
  * `ordered::Bool = false`: 出力で入力行の順序を保持するかどうか
  * `progress::Bool = true`: プログレスバーを表示するかどうか
  * `limit::Union{Int, Nothing} = nothing`: 処理する最大行数
  * `optional_api_params::Dict{Symbol, Any} = Dict{Symbol, Any}()`: APIに渡す追加のパラメータ
  * `rate_limit_semaphore::Union{Base.Semaphore, Nothing} = nothing`: レート制限のためのオプションのセマフォ
  * `command::Union{Symbol, Nothing} = nothing`: 特定のジオコーディングコマンドを強制する

      * `:forward`: 前方ジオコーディングを強制
      * `:reverse`: 逆ジオコーディングを強制
      * `nothing`: 入力列に基づいて自動検出

# 戻り値

  * `nothing`: 関数は結果を出力ファイル/ストリームに書き込みます

# 例外

  * `BatchProcessingError`: バッチ処理中にエラーが発生した場合
  * `InvalidInputError`: 入力パラメータが無効な場合

# 例

```

julia

# ファイルパスを使用した基本的な使用法

batch_geocode(     geocoder,     "input.csv",     "output.csv" )

# カスタムオプションを使用して

batch*geocode(     geocoder,     "input.csv",     "output.csv",     workers=8,     input*columns=[2],  # ジオコーディングに2列目を使用     add*columns=["formatted", "geometry.lat", "geometry.lng", "components.country"],     on*error=:skip,     ordered=true,     progress=true )

# 列1と2に座標がある逆ジオコーディング

batch*geocode(     geocoder,     "coordinates.csv",     "addresses.csv",     input*columns=[1, 2],  # 緯度と経度の列     command=:reverse ) ```
