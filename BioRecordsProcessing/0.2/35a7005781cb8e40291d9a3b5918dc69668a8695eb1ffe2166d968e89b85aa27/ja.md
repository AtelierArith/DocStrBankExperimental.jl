```julia
Reader(record_module::Module, file_provider::F) where {F <: AbstractFileProvider}
```

ディスク上のファイルまたはディレクトリを読み取り、`record_module.Record`型のレコードを生成します。第二引数は`File`または`Directory`であることができます。

文字列が渡されると、第二引数は`File`にデフォルト設定されます。

```@example
Reader(FASTX.FASTA, "test.fa")
Reader(FASTX.FASTA, File("test.fa"))
Reader(FASTX.FASTQ, Directory("data/", "*.fastq"))
```
