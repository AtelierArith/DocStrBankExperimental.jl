```
FastaReader{T}(file::Union{AbstractString,IO})
```

これは、FASTAファイルを1エントリずつ解析できるオブジェクトを作成します。`file`はプレーンテキストファイルまたはgzip圧縮ファイルであり（内容から自動的に検出されます）、型`T`はシーケンスの出力タイプを決定します（詳細については[シーケンスストレージタイプ](@ref)セクションを参照）し、デフォルトは`String`です。

データは`FastaReader`オブジェクトを反復処理することで読み取ることができます：

```julia
for (name, seq) in FastaReader("somefile.fasta")
    # nameとseqを使って何かをする
end
```

示されているように、イテレータは説明（常に`String`）とデータ（`FastaReader`オブジェクトを作成する際に設定された型（例：`FastaReader{Vector{UInt8}}(filename)`）を含むタプルを返します。

`FastaReader`型には、これまでに解析されたエントリの数を含むフィールド`num_parsed`があります。

データを読み取る他の方法としては、[`readentry`](@ref)および[`readfasta`](@ref)関数があります。
