```
HTMLPrinter(buf::IO; root_class="", root_tag="pre", callback=nothing)
```

`MIME"text/html"` 出力用のプリンタを作成します。

# 引数

  * `buf`: ANSI エスケープコードを含むテキストを持つソース `IO` オブジェクト。
  * `root_class`: ルート要素の `class` 属性値。
  * `root_tag`: ルート要素のタグ名。
  * `callback`: コールバックメソッド（下記参照）。

# コールバックメソッド

```
callback(io::IO, printer::HTMLPrinter, tag::String, attrs::Dict{Symbol, String})
```

`callback` メソッドは、HTML タグを書き込む直前に呼び出されます。

## コールバック引数

  * `io`: 目的の `IO` オブジェクト。
  * `printer`: 使用中の `HTMLPrinter`。
  * `tag`: 書き込まれる HTML タグ。閉じタグの場合、接頭辞に "/" が付きます。
  * `attrs`: 属性のペア（例: `:class`, `:style`）の `Symbol` とその値の `String` からなる辞書。

## コールバックの戻り値

戻り値が `nothing` の場合、プリンタは呼び出し後に `tag` と `attrs` に従って `io` に HTML タグを書き込みます。戻り値が `nothing` でない場合、このデフォルトの書き込みは防止されます。
