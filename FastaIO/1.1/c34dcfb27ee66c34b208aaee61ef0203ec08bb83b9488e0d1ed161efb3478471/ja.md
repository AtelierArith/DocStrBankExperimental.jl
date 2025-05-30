```
writefasta(filename::String, data, [mode::String = "w"]; check_description=true)
```

この関数はデータをFASTAファイルにダンプし、[FASTA形式](@ref)のセクションで詳述された仕様に従って自動的にフォーマットします。`data`は反復可能なものであり、反復時に`(description, sequence)`タプルを生成する必要があります。ここで、`description`は`String`に変換可能であり、`sequence`はASCII文字に変換可能な要素を生成する任意の反復可能オブジェクト（例：`String`、`Vector{UInt8}`など）である必要があります。

例:

```julia
writefasta("somefile.fasta", [("GENE1", "GCATT"), ("GENE2", "ATTAGC")])
writefasta("somefile.fasta", ["GENE1" => "GCATT", "GENE2" => "ATTAGC"])
```

`filename`が`.gz`で終わる場合、結果はgzip圧縮ファイルになります。

`mode`フラグは`filename`の開き方を決定します。既存のファイルにデータを追加するには`"a"`を使用します。

`check_description=false`というキーワードを設定すると、説明行が長すぎる場合に表示される警告メッセージを無効にできます。
