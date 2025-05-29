```
compare_plans(left, right; options)
compare_plans(file, left, right; options)
compare_plans(Base.stdout, left, right; options)
```

2つのプランを比較する要約情報を持つMVTSeriesを返します。MVTSeriesの各セルには、以下のルブリックに対応する整数値があります：

  * 0 -> 両方のプランで内生的。
  * 1 -> 左のプランのみ外生的。
  * 2 -> 右のプランのみ外生的。
  * 3 -> 両方のプランで外生的。

MVTSeriesにはプラン間の重複のみが含まれます。いずれかのプランにのみ含まれる変数、ショック、期間は返されるMVTSeriesの一部にはなりません。

詳細な比較は、`outfile`または`io`引数を使用してファイルに印刷することもできます。

### オプション

  * `outfile=""` - 提供された場合、詳細な比較をターゲットのoutfileパスに保存します。
  * `io=nothing` - 特定のiobufferに詳細な比較を出力します。
  * `diff=false` - プラン間で異なる変数とショックのみを詳細な比較に含めます。
  * `alphabetical=false` - 変数をソートするには`true`に設定します。デフォルトでは、変数は左のプランと同じ順序でリストされます。
  * `exog_mark="X"` - 外生的な値をマークするための短い文字列（理想的には1文字）。
  * `endo_mark="~"` - 内生的な値をマークするための短い文字列（理想的には1文字）。
  * `missing_mark="."` - 1つのプランから変数が欠けている場合に表示する短い文字列（理想的には1文字）。
  * `delim=" "` - デリミタ。CSVファイルにするには`","`を使用します。
  * `pagelines=0` - ページネーションを有効にするために正の整数に設定します。数はヘッダー行（範囲を含む行）を繰り返す行数として解釈されます。
  * `summary=false` - プランの違いに関する要約をstdoutに印刷します。
  * `legend=false` - 比較マトリックスの凡例をstdoutに印刷します。
