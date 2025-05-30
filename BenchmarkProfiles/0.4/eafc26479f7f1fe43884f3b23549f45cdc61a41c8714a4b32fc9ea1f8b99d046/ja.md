```
performance_profile(b, T, labels; logscale=true, title="", sampletol=0.0, drawtol=0.0; kwargs...)
```

指定されたバックエンドを使用してパフォーマンスプロファイルを生成します。

## 引数

  * `b :: AbstractBackend`: プロットを生成するために使用されるバックエンド。
  * `T :: Matrix{<: Number}`: `T`の各列はソルバーのパフォーマンスデータを定義します（正の値であり、小さいほど良い）。特定の問題での失敗は負の値、無限値、または`NaN`で表されます。
  * `labels :: Vector{AbstractString}`: 凡例を生成するために使用される各プロファイルのラベルのベクター。空の場合、`labels`は`["column 1", "column 2", ...]`に設定されます。

## キーワード引数

  * `logscale :: Bool=true`: 対数（基数2）パフォーマンスプロットを生成します。
  * `title :: AbstractString=""`: プロットのタイトルを設定します。
  * `sampletol :: Float64 = 0.0`: 大量の問題を使用する際にパフォーマンスのためにプロファイルをダウンサンプリングするために使用される許容誤差。
  * `drawtol :: Float64 = 0.0`: 2つのパフォーマンス測定の間で引き分けを宣言するための許容誤差。
  * `linestyles::Vector{Symbol}`: バックエンドがサポートしている場合、プロファイルに使用するラインスタイルのベクター。

他のキーワード引数は、対応するバックエンドのプロットコマンドに渡されます。
