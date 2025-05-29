```
displaytable([io::IO], v::AbstractVector{T}; kwargs...)
```

ベクトルの要素をコンパクトな表形式で表示します。`io` 引数はデフォルトで `stdout` に設定されています。

# キーワード引数

  * padding: 列データ間の最小スペース数。デフォルト値は 2 です。
  * index: セル値の前にインデックスを追加します。デフォルト値は `false` です。
  * indexsep: インデックスとセル値を区切る文字列。デフォルト値は `:` です。
  * align: `:left` または `:right` のいずれか。デフォルト値は `:left` です。
  * orientation: `:column` または `:row` のいずれか。デフォルト値は `:column` です。
  * formatter: 値を受け取り文字列を返すカスタムフォーマッタ。デフォルト値は `string` 関数です。
  * displaywidth: カスタム表示幅。デフォルト値は 0 で、システムはターミナルのサイズを使用します。

# 例

```
displaytable([string("randomstr", i) for i in 1:56])

using Formatting
foo = generate_formatter("%7.5f")
displaytable(rand(100); padding=5, align=:right, formatter=foo, index=true, indexsep=" -> ")
```
