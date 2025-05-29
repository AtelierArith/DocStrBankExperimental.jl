```
R = rescale(A; low=0.0, up=1.0; inputmin=nothing, inputmax=nothing, stretch=false, type=nothing)
```

  * `A`: は GMTgrid、GMTimage、Matrix{AbstractArray} またはファイル名のいずれかです。後者の場合、ファイルは `gmtread` を呼び出して読み込まれ、ファイル拡張子に基づいて自動的に読み込み方法が決定されます... 100% 安全ではありません。
  * `rescale(A)` は配列 `A` のすべてのエントリを [0,1] に再スケーリングします。
  * `rescale(A,low,up)` は A のすべてのエントリを区間 [low,up] に再スケーリングします。
  * `rescale(..., inputmin=imin)` は入力範囲の下限 `imin` を設定します。 `imin` より小さい入力値は `imin` に置き換えられます。デフォルトは min(A) です。
  * `rescale(..., inputmax=imax)` は入力範囲の上限 `imax` を設定します。 `imax` より大きい入力値は `imax` に置き換えられます。デフォルトは max(A) です。
  * `rescale(..., stretch=true)` はヒストグラムへの呼び出しを通じて [inputmin inputmax] を自動的に決定し、ヒストグラムのストレッチのための良い制限を見つけようとします。 `stretch=(imin,imax)` の形式では、入力制限を直接指定できます。
  * `type`: スケーリングされた配列をこのデータ型に変換します。有効なオプションはすべての符号なし型（例： `UInt8`）です。デフォルトでは、`A` が AbstractFloat の場合は同じデータ型を返し、`A` が整数の場合は Float64 を返します。

`A` が浮動小数点の GMTgrid の場合は GMTgrid を、`A` が GMTimage で `type` が使用されている場合は GMTimage を、それ以外の場合は Float32|64 の配列を返します。
