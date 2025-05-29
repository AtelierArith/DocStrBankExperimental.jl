```
FastaWriter(filename::AbstractString, [mode::String = "w"])
FastaWriter([io::IO = stdout])
FastaWriter(f::Function, args...)
```

これは、[`write`](@ref)および[`writeentry`](@ref)関数を介して、[The FASTA format](@ref)というセクションで詳述された仕様に準拠したフォーマットされたFASTAファイルを書き込むことができるオブジェクトを作成します。

3番目の形式では、do-notationを使用することができます：

```julia
FastaWriter("somefile.fasta") do fw
    # ファイルを書き込む
end
```

これは、書き込みの最後に[`close`](@ref)関数が呼び出されることを保証するため、強く推奨されます：これは重要であり、そうしないと不完全なファイルが生成される可能性があります（これはファイナライザーによって行われるため、`FastaWriter`オブジェクトがスコープを外れ、ガーベジコレクトされても自動的に発生しますが、Juliaが終了した場合にこれが発生する保証はありません）。

`filename`が`.gz`で終わる場合、結果はgzip圧縮されます。

`mode`フラグは、ファイルのオープニングモードを設定するために使用できます；既存のファイルに追加するには`"a"`を使用します。

`FastaWriter`オブジェクトには、現在書き込まれているエントリの番号を格納する`entry::Int`フィールドがあります。

オブジェクトを作成した後、`check_description`フィールドを`false`に設定することで、説明行が長すぎるときに表示される警告を無効にすることができます。
