```
scrape_tables(url)
scrape_tables(url, cell_transform[=nodeText])
scrape_tables(url, cell_transform[=nodeText], header_transform[=nodeText])
```

この関数は、`url`から`<table>`タグでラップされた適切に形成されたテーブルをスクレイピングし、それらをベクターとして返します。

# 引数

```
- `url`: テーブルを探すためのURL
- `cell_transform`: デフォルトでは、`<td>`でラップされた各テーブルセルは、呼び出し可能な（すなわち、`Function`または型定義）`cell_transform`によって変換されます。デフォルトの`cell_transform`は`Cascadia.nodeText`で、ノードのテキストを抽出します。より高度な処理のために、単にセルを`Gumbo.HTMLNode`型として抽出するために`identity`を使用することをお勧めします。例: `scrape_tables(url, identity)`
- `header_transform`: デフォルトでは、`<th>`でラップされた各テーブルヘッダーは、呼び出し可能な（すなわち、`Function`または型定義）`header_transform`によって変換されます。デフォルトの`header_transform`は`Cascadia.nodeText`で、ノードのテキストを抽出します。より高度な処理のために、単にセルを`Gumbo.HTMLNode`型として抽出するために`identity`を使用することをお勧めします。例: `scrape_tables(url, identity, identity)`
```

# 戻り値

```
`Vector{TableScraper.Table}`
```

`TableScraper.Table`は、Tables.jl互換の行アクセス可能な型です。したがって、必要に応じて別のTables.jl互換の型に変換できます。例: `DataFrame.(scrape_tables(url))`は`DataFrame`のベクターを返します。
