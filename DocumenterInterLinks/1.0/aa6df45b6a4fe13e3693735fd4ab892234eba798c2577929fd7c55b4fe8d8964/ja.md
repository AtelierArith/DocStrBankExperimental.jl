`Documenter.jl`で外部リンクを有効にするためのプラグイン。

```julia
links = InterLinks(
    mappings...;
    default_inventory_file="objects.inv",
    alias_methods_as_function=true,
)
```

は、[`Documenter.makedocs`](@extref)の`plugins`キーワード引数の要素として渡す必要があるプラグインオブジェクトをインスタンス化します。これにより、プロジェクトのドキュメント内で`@extref`リンクが解決されるようになります。詳細については、[Syntax](@ref)ドキュメントを参照してください。`mappings`はプロジェクト名をプロジェクトのルートURLおよびインベントリに接続します。例えば、

```julia
links = InterLinks(
    "Julia" => (
        "https://docs.julialang.org/en/v1/",
        "https://docs.julialang.org/en/v1/objects.inv",
        joinpath(@__DIR__, "inventories", "Julia.toml")
    ),
    "Documenter" => "https://documenter.juliadocs.org/stable/objects.inv",
    "sphinx" => "https://www.sphinx-doc.org/en/master/";
)
```

詳細は以下をご覧ください。

# 引数

`InterLinks`プラグインは、プロジェクト名をプロジェクトのルートURLおよびインベントリの場所にマッピングします。各プロジェクト名は、英数字のASCII文字列でなければなりません。Juliaプロジェクトの場合、`.jl`サフィックスを除いたパッケージの名前である必要があります。例えば、[Documenter.jl](https://documenter.juliadocs.org/)の場合は`"Documenter"`です。Pythonプロジェクトの場合は、プロジェクトのメインモジュールの名前である必要があります。

ルートURL / インベントリの場所（マッピングの値）は、以下のいずれかの形式で指定できます（一般的なものから少ないものへ）：

  * プロジェクトのルートURLを含む単一の文字列。例えば、上記の例の`sphinx`エントリです。URLはスラッシュで終わる必要があります。これは、指定されたルートURLの直下にある`default_inventory_file`に対応する名前のインベントリファイルを探します。これが最も一般的な形式です。
  * 文字列のタプルで、最初の要素がプロジェクトのルートURLで、すべての後続の要素がインベントリファイルへの場所（URLまたはローカルファイルパス）です。最初に到達可能なインベントリファイルが使用されます。これにより、例えば、オンラインのインベントリファイルの場所にアクセスできない場合にローカルのインベントリファイルをフォールバックとして定義できます。上記の例の`"Julia"`エントリのように。
  * インベントリファイルのURLを含む単一の文字列。例えば、上記の例の`"Documenter"`エントリです。インベントリ内のすべてのURIが取得されるルートURLは、インベントリURLの最終スラッシュまでの部分、つまりこの場合は`"https://documenter.juliadocs.org/stable/"`です。文字列はURLでなければならず、ローカルファイルパスではないことに注意してください。ファイルパスにはプロジェクトのルートURLに関する暗黙の情報が含まれていません。
  * [`DocInventories.Inventory`](@extref)インスタンス。動的に構築されたインベントリを使用するのに便利です。

# キーワード引数

`InterLinks`のキーワード引数は実験的であり、マイナーなバージョンで変更される可能性があります。

  * `default_inventory_file`: "インベントリの場所"がルートURLとして指定された場合に使用するインベントリファイルのファイル名。SphinxとDocumenterの両方が自動的に`objects.inv`を書き込むため、これをデフォルトの`"objects.inv"`以外に設定する理由はほとんどありません。
  * `alias_methods_as_function`: `true`（デフォルト）の場合、ファイルまたはURLから読み込まれたインベントリに対して、あらゆる`:jl:method`に対して、あらゆる`:jl:function:`エイリアスを自動的に追加します。このエイリアスがあいまいでない場合に限ります。これは、Documenterが`@autodoc`ブロックからメソッドのドキュメント文字列を優先的に生成することを考慮しています。たとえそのメソッドが基になる関数の唯一のメソッドであってもです。例えば、[`Documenter.Selectors.dispatch`](@extref)関数には、次のように非常に長い参照を必要とするメソッドのドキュメント文字列しかありません。

    ```
    [`Documenter.Selectors.dispatch`](@extref `Documenter.Selectors.dispatch-Union{Tuple{T}, Tuple{Type{T}, Vararg{Any}}} where T<:Documenter.Selectors.AbstractSelector`)
    ```

    エイリアスを使用すると、これを```[`Documenter.Selectors.dispatch`](@extref)```に短縮できます。同じ関数の複数のメソッドにドキュメント文字列がある場合や、既存の関数のドキュメント文字列がある場合は、エイリアスは作成されません。

# プロパティ

  * `names`: プロジェクト名のリスト
  * `inventories`: プロジェクト名から[`DocInventories.Inventory`](@extref)インスタンスへの辞書
  * `rx`: 有効な`@extref`式に一致する[`Regex`](@extref Julia Base.Regex)

`InterLinks`オブジェクトは、例えば`links["project1"]`がそのプロジェクトの[`DocInventories.Inventory`](@extref)を返すように、（読み取り専用の）順序付き辞書としても機能します。

# 検索

特定のインベントリ内での自由形式の検索は、例えば次のように可能です。

```julia
links["Julia"](search)
```

検索に関する議論は、[`DocInventories.Inventory`](@extref)ドキュメントを参照してください。このような検索は、一致する[`DocInventories.InventoryItem`](@extref)インスタンスのリストを返します。

さらに、

```
links(search)
```

は、*すべての*インベントリを横断して検索を行うことができます。これにより、一致するアイテムを参照するために使用できる`@extref`文字列のリストが返されます。

# メソッド

  * [`find_in_interlinks(links, extref)`](@ref) – `extref`のURLを見つける

# 参照

`InterLinks`マッピングは、[Sphinx](@extref sphinx :doc:`index`)の[`intersphinx_mapping`](@extref)設定を意図的に思い起こさせるものです。
