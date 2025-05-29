```julia
print_ascii_plot(
    io,
    ubc;
    canvas_width,
    p_colname,
    bin_colname,
    α,
    count_colname,
    padding,
    ess_correction
)

```

与えられた単変量ビンカウントからの統計を使用して、`io`にASCIIプロットを印刷します。最初の引数が`String`の場合、出力を印刷するのではなく文字列として返します。

# キーワード引数

  * `canvas_width`: プロットのキャンバスの幅
  * `p_colname`: p値の列名（実際に印刷される値は`-log10(p)`です）
  * `bin_colname`: ビンインデックスの列名
  * `count_colname`: カウントの列名
  * `α`: 量子`α`と`1-α`にマーカー（`(`と`)`を含む）が配置されます
  * `padding`: キャンバスの拡大係数

`ess_correction = true`（デフォルト）である場合、標準偏差は有効サンプルサイズを使用して計算されます。
