```
mosaic!(f, dest::Union{Raster,RasterStack}, regions...; kw...)
mosaic!(f, dest::Union{Raster,RasterStack}, regions; kw...)
```

`regions` の `Raster` または `RasterStack` を `dest` に結合し、重複する領域を結合するために関数 `f` を使用します。

# 引数

  * `f`: `regions` が重複する値のための縮小関数。一般的な基本関数（`mean`、`sum`、`prod`、`first`、`last`、`minimum`、`maximum`、`length`）は最適化されており、多くのメモリまたはディスクベースのファイルで動作しますが、ユーザー定義の関数は、`op` がキーワードとして渡されない限り、大規模なスケールでは失敗する可能性があります。
  * `regions`: `Raster` または `RasterStack` のイテラブル。多くの領域がある場合、`Tuple` やスプラットを使用するよりも、`AbstractArray` を使用する方が通常は良いです。
  * `dest`: `Raster` または `RasterStack`。オープンされたディスクベースの `Raster` である可能性があり、結果はディスクに書き込まれます。現在のアルゴリズムでは、読み取り速度は遅いです。

# キーワード

  * `missingval`: 空の領域を埋め、最初の領域の `missingval` にデフォルト設定されます。
  * `op`: 縮小のための演算子、例えば `sum` のための `add_sum`。`sum` のような一般的なメソッドについては、これらは知られており、自動的に検出されますが、他の関数のために手動で提供することもでき、大規模なスケールでも動作し続けます。
  * `atol`: インデックス値間の比較のための絶対許容誤差。これは、浮動小数点エラーによる範囲値のわずかな違いのためにしばしば必要です。非浮動小数点次元には適用されません。許容誤差のタプルを渡すことができ、次元の順序に一致させることができます。
  * `progress`: 進行状況バーを表示します。デフォルトは `true` で、隠すには `false` にします。
  * `read`: 書き込む前に遅延ラスタ領域を `read` します。これは、ソースと宛先ラスタ間のチャンク整列の問題がある場合に役立つかもしれません。デフォルトは `false` です。

警告: この機能は実験的です。将来のバージョンで変更される可能性があり、すべてのケースで100%信頼できるわけではありません。問題が発生した場合は、GitHubの問題を報告してください。
