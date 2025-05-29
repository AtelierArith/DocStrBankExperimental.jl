プロジェクトドキュメントにおけるリンクターゲットのインベントリ。

```julia
inventory = Inventory(
    source;
    mime=auto_mime(source),
    root_url=root_url(source)
)
```

は、指定された `source` からインベントリファイルを読み込みます。`source` はURLまたはローカルファイルへのパスであることができます。URLの場合、`timeout`（ネットワーク接続の待機時間）、`retries`（再試行回数）、および `wait_time`（各再試行の間に追加で待機する秒数）を指定できます。`source` は指定されたmimeタイプのデータを含む必要があります。デフォルトでは、mimeタイプはファイル拡張子から派生します（[`auto_mime`](@ref)を介して）。

`Inventory` は、プロジェクトのオンラインドキュメント内のすべてのオブジェクト、セクション、または他のリンク可能なアイテムを表す [`InventoryItems`](@ref InventoryItem) のコレクションとして機能します。

または、

```julia
inventory = Inventory(; project, version="", root_url="", items=[])
```

必須の `project` 引数を使用して、`items` にある [`InventoryItems`](@ref InventoryItem) で `inventory` をインスタンス化します。`items` が指定されていない場合、結果として得られる空の `inventory` に対して、後で [`push!`](@extref Julia Base.push!) を介して [`InventoryItems`](@ref InventoryItem) を追加できます。

# 属性

  * `project`: プロジェクトの名前
  * `version`: プロジェクトのバージョン（例: `"1.0.0"`）
  * `root_url`: 任意の [`InventoryItem`](@ref) の `item.uri` が相対的であるルートURL。空でない場合は、`"https://"` で始まり、スラッシュで終わる必要があります。
  * `source`: インベントリが読み込まれたURLまたはファイル名。
  * `sorted`: アイテムがその `name` 属性によってソートされているかどうかを示すブール値。これは、URLまたはファイルから読み込まれたすべてのインベントリに対して `true` であり、手動でインスタンス化されたインベントリに対しては `false` です。

`source` と `sorted` は情報属性のみであり、2つの `Inventory` オブジェクトを比較する際には無視されます。

# アイテムアクセス

アイテムは、反復（`for item in inventory`）、数値インデックス（`inventory[1]`, `inventory[2]`, … `inventory[end]`）、またはルックアップ（`inventory[name]` または `inventory[spec]`）を介してアクセスできます。ここで、`spec` は形式 ```":[domain:]role:`name`"``` の文字列であり、[`InventoryItem`](@ref) の `spec` に関する議論を参照してください。ルックアップは [`find_in_inventory`](@ref) に委任され、`quiet=true` であり、[`item.priority`](@ref InventoryItem) を考慮します。

# 検索

インベントリは、`inventory(search; include_hidden_priority=true)` を呼び出すことで検索できます。これにより、`spec(item)` または `repr(item; context=(:full => true))` に `search` を含むすべてのアイテムのリストが返されます。通常、`search` は文字列または [`Regex`](@extref Julia man-regex-literals) です。一般的な検索のいくつかの例：

  * 形式 ```":domain:role:`name`"``` の `spec`、完全、部分的、または正規表現として。
  * プロジェクトのドキュメント内のページのURLの一部、文字列として
  * プロジェクトのドキュメント内のどこかに表示されるセクションのタイトル。

検索結果は [`abs(item.priority)`](@ref InventoryItem) によってソートされます。`include_hidden_priority=false` の場合、負の `item.priority` 値は省略されます。

# メソッド

  * [`find_in_inventory(inventory, name)`](@ref find_in_inventory) – `inventory` 内の単一アイテムを見つける
  * [`save(filename, inventory; mime=auto_mime(filename))`](@ref save) – 任意のサポートされている出力形式で `inventory` をファイルに書き込む。
  * [`show_full(inventory)`](@ref) – REPL で省略されていないインベントリを表示する（理想的には [`TerminalPager`](https://ronisbr.github.io/TerminalPager.jl/) を介して）
  * [`uri(inventory, key)`](@ref uri(::Inventory, key)) – `inventory` からアイテムの完全なURIを取得する。
  * [`push!(inventory, items...)`](@extref Julia Base.push!) – 既存の `inventory` に [`InventoryItems`](@ref InventoryItem) を追加する。
  * [`append!(inventory, collections...)`](@extref Julia Base.append!) – 既存の `inventory` に [`InventoryItems`](@ref InventoryItem) のコレクションを追加する。
  * [`collect(inventory)`](@extref Julia Base.collect-Tuple{Any}) – インベントリを標準の `Vector` の [`InventoryItems`](@ref InventoryItem) に変換する。
  * [`set_metadata(inventory)`](@ref) – `project` と `version` メタデータを修正する。
  * [`sort(inventory)`](@extref Julia Base.sort) – ソートされていないインベントリをソートされたものに変換する。
