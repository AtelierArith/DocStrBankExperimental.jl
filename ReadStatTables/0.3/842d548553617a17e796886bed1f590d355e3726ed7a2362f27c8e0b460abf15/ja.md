```
writestat(filepath, table; ext = lowercase(splitext(filepath)[2]), kwargs...)
```

`Tables.jl`互換の`table`を`filepath`に`ReadStat`がサポートするデータファイルとして書き込みます。ファイル形式は`filepath`に含まれる拡張子に基づいて決定され、`ext`キーワードによって上書きされる可能性があります。

ユーザー提供の`table`は、`ReadStat`ライターによって処理される前に最初に[`ReadStatTable`](@ref)に変換されます。したがって、特にメタデータのために書き込まれる内容を細かく制御するには、`writestat`に渡す前に[`ReadStatTable`](@ref)（`DataFrames.jl`の`DataFrame`など、他のテーブルタイプから変換された可能性があります）を直接操作することができます。あるいは、`writestat`に[`ReadStatTable`](@ref)のコンストラクタが受け入れる任意のキーワード引数を渡すこともできます。ライターが終了した後に処理された実際の[`ReadStatTable`](@ref)が返されます。

# サポートされているファイル形式

  * Stata: `.dta`
  * SAS: `.sas7bdat`および`.xpt`（注: SASは、ReadStatに関する既知の制限のため、生成された`.sas7bdat`ファイルを認識しない可能性があります。）
  * SPSS: `.sav`および`por`

# 変換

データ値については、Juliaオブジェクトは数値または文字列のいずれかの最も近い`ReadStat`タイプに変換されます。ただし、出力ファイルのファイル形式によっては、最も近い`ReadStat`タイプがサポートされていない場合、データ列は異なるタイプで書き込まれることがあります。

メタデータについては、ユーザー提供の`table`が[`ReadStatTable`](@ref)でない場合、`metadata`および`colmetadata`インターフェースを介して[`ReadStatMeta`](@ref)または[`ReadStatColMeta`](@ref)のメタデータフィールドに一致するキーを持つテーブルレベルまたは列レベルのメタデータを収集しようとします。`table`が[`ReadStatTable`](@ref)である場合、関連するメタデータは出力ファイルの形式と互換性がある限り書き込まれます。[`LabeledArray`](@ref)に関連付けられた値ラベルは、メタデータで値ラベルの辞書の名前が指定されていない場合でも常に保持されます（デフォルトでは列名が使用されます）。`DataAPI.refpool`を利用する配列型の列（例: `CategoricalArray`および`PooledArray`）の場合、値ラベルはデフォルトで自動的に生成され（キーワード`refpoolaslabel`が`true`に設定されます）、`getindex`によって返される値の代わりに基礎となる数値参照値がファイルに書き込まれます（値ラベルが添付されます）。
