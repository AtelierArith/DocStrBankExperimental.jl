```
writeentry(fw::FastaWriter, description::AbstractString, sequence)
```

この関数は、[FASTA形式](@ref)というセクションで詳述された仕様に従って、FASTAファイルに1つのエントリを書き込みます。`description`は最初の`'>'`文字なしで指定します。`sequence`は、要素がASCII文字に変換可能な任意の反復可能オブジェクトである必要があります。

例:

```julia
FastaWriter("somefile.fasta") do fw
    for (desc,seq) in [("GENE1", "GCATT"), ("GENE2", "ATTAGC")]
        writeentry(fw, desc, seq)
    end
end
```
