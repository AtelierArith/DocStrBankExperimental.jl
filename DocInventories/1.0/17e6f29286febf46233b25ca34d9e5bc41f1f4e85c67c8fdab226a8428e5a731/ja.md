[`Inventory`](@ref) 内のアイテム。

```julia
item = InventoryItem(; name, role, uri, priority=1, domain="jl", dispname="-")
```

は、`name` によって参照されるプロジェクトドキュメント内のリンク可能なアイテムを表します。`domain` と `role` は [Sphinx プロジェクト](@extref sphinx usage/domains/index) からその意味を引き継ぎ、これらのパラメータの詳細については *Attributes* を参照してください。また、`priority` と `dispname` についても同様です。`uri` はプロジェクトのルートに対して相対的であり、`InventoryItem` を含む `inventory` の [`Inventory.root_url`](@ref Inventory) であるべきです。

便利なことに、`InventoryItem` はマッピング `spec => uri` からもインスタンス化できます。ここで ```spec=":domain:role:`name`"``` は Sphinx の [クロスリファレンス構文](@extref sphinx usage/referencing) を借用しています：

```julia
item = InventoryItem(
    ":domain:role:`name`" => uri;
    dispname=<name>,
    priority=(<domain == "std" ? -1 : 1>)
)
```

`domain` はオプションです：もし ```spec=":role:`name`"``` の場合、`domain` は `role="label"` または `role="doc"` の場合は `"std"` となり、それ以外は `"jl"` となります。`role` はコードオブジェクトに対して必須です。非コードオブジェクトの場合、

```julia
item = InventoryItem(
    "title" => uri;
    dispname=<title>,
    priority=-1
)
```

はプロジェクトのドキュメント内のセクションヘッダーへのリンクを示します。`name` はタイトルのスラッグ化されたバージョンとなり、`item` は ```item = InventoryItem(":std:label:`name`" => uri; dispname=title, priority=-1)``` と同等になります。

# 属性

  * `name`: 参照用のオブジェクト名。コードオブジェクトの場合、これは完全修飾名であるべきです。セクション名の場合、セクションタイトルのスラッグ化されたバージョンである可能性があります。ゼロ以外の長さでなければなりません。
  * `domain`: [Sphinx ドメイン](@extref sphinx usage/domains/index) の名前。Julia コードオブジェクトの場合は `"jl"`（デフォルト）、Python コードオブジェクトの場合は `"py"`、セクション名などのテキストオブジェクトの場合は `"std"` であるべきです。ゼロ以外の長さでなければならず、空白やコロンを含んではいけません。
  * `role`: ドメイン固有の [role](@extref sphinx :term:`role`) ([type](@extref sphinx sphinx.domains.ObjType))。ゼロ以外の長さでなければならず、空白を含んではいけません。
  * `priority`: 検索結果での配置のための整数フラグ。[`Inventory`](@ref) での検索時、[`Inventory`](@ref) でのアイテムアクセス時、[`find_in_inventory`](@ref) で使用されます。サポートされているフラグ値は以下の通りです：

      * `1`: "デフォルト" プライオリティ。`"std"` ドメインにないすべてのオブジェクト（つまり、`"jl"` ドメインのすべての "コード" オブジェクト）にデフォルトで使用されます。
      * `0`: オブジェクトは重要
      * `2`（またはそれ以上）: オブジェクトは重要でない
      * `-1`（またはそれ以下）: オブジェクトは "隠されている"（検索から省略される可能性があります）。`std` ドメインのすべてのオブジェクト（セクションタイトル）にデフォルトで使用されます。

    詳細については [`find_in_inventory`](@ref) を参照してください。上記の意味は [Sphinx](https://github.com/sphinx-doc/sphinx/blob/2f60b44999d7e610d932529784f082fc1c6af989/sphinx/domains/__init__.py#L370-L381) で使用されているものと一致します。
  * `uri`: オブジェクトのドキュメントの場所に対する URI で、`item` を含むインベントリファイルの場所に対して相対的です。空白を含んではいけません。`name` のプレースホルダーを示すために `"$"` で終わることがあります（通常は `"#$"` として、`name` に一致する HTML アンカーのため）。
  * `dispname`: オブジェクトの完全なプレーンテキスト表現。表示名が `name` と同一である場合は `"-"` である可能性があります（コードオブジェクトの場合はそうであるべきです）。セクションタイトルの場合、これはフォーマットなしのタイトルのプレーンテキストであるべきですが、スラッグ化されてはいけません。

# メソッド

  * [`uri`](@ref) – 完全な URI を抽出し、`$` プレースホルダーを解決し、適用可能な場合は `root_url` を前に付加します。
  * [`dispname`](@ref) – `dispname` を抽出し、適用可能な場合は `"-"` 短縮形を解決します。
  * [`spec`](@ref) – アイテムに関連付けられた仕様文字列 ```":domain:role:`name`"``` を返します。
