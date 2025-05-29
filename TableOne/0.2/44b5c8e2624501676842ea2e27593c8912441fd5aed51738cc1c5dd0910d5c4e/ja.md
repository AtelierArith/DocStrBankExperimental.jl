```
tableone(data, strata[, vars]; <keyword arguments>)
```

原稿の表1として使用できる要約表を生成します。

## 引数

  * `data`: 表に含めるデータを含む `DataFrame`
  * `strata`: 表でデータを層別化するための変数（`data` の列）
  * `vars`: 表にリストされる変数。指定しない場合は `Symbol.(names(data))` にデフォルト設定されます。

# キーワード引数

## 変数の種類

これらはすべて `vars` と同じ型で指定する必要があります。たとえば、`vars` が `Vector{Symbol}` の場合、これらもそれぞれ `Vector{Symbol}` である必要があります。これらの引数のいずれかに供給された変数は、メインの `vars` 引数には表示されません。

  * `binvars`: バイナリ変数 – 変数は1行を取り、選択されたレベルの **数 (%)** を表示します（以下の `binvardisplay` を参照）
  * `catvars`: カテゴリ変数 – 変数の各レベルが別の行に表示され、そのカテゴリの **数 (%)** が示されます
  * `npvars`: ノンパラメトリック変数 – **中央値 [1st–3rd 四分位数]** を表示します
  * `paramvars`: パラメトリック変数 – **平均 (標準偏差)** を表示します
  * `cramvars`: `binvars` のバリエーションで、テーブルの1行に両方のレベルを表示します

これらの引数のいずれにも含まれていない変数は、変数の内容が `<:Union{<:Number, Missing}` の場合は `mean (standard deviation)` として表示され、それ以外の場合はカテゴリとして表示されます。

## 追加のキーワード引数

  * `addnmissing=true`: 各変数の欠損値を持つレコードの数を含めます。`true` の場合、欠損 `strata` 値の数も表示されます
  * `addtestname=false`: p値を計算するために使用された統計テストの名前を表示します。このオプションは `pvalues == true` の場合にのみ効果があります
  * `addtotal=false`: すべての `strata` にわたる合計の列を含めます
  * `binvardisplay=nothing`: オプションで、バイナリ値の表示レベルを選択するための `Dict`。リストされていない変数は `maximum(skipmissing(.))` で選択された値を使用します
  * `digits=1`: 平均、標準偏差、パーセンテージの小数点以下に表示される桁数
  * `includemissingintotal=false`: 合計列に層別化変数が欠損しているレコードを含めます。このオプションは `addtotal == false` の場合には効果がありません
  * `pdigits=3`: p値の小数点以下に表示される桁数
  * `pvalues=false`: 表の各変数に対して有意なテスト p値を表示するかどうか
  * `varnames=nothing`: オプションで、`data` の列タイトルとは異なる変数の名前の `Dict`。形式は `Dict(:columnname => "印刷する名前")` です。含まれていない変数は列名でリストされます

例についてはドキュメントを参照してください。
