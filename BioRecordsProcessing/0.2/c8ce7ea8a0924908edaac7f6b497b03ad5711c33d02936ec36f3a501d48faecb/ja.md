```julia
Writer(record_module::Module, output_directory::String; 
    suffix = "", 
    paired = false, 
    second_in_pair = nothing, 
    extension = nothing, 
    header = nothing
)
```

処理関数の出力をファイルに書き込みます。最初の引数は `Record` 型を所有するモジュール（例：`FASTX.FASTA`、`VCF` など）で、2番目の引数は出力ディレクトリです。ファイル名はソースによって決定され、オプションのサフィックスを追加できます。出力の型が出力の型と異なる場合（例：SAMからBAM）、拡張子（".bam"）を指定する必要があります。SAMおよびBAMの場合、SAM.Headerを提供する必要があります。

既存のファイルを上書きしないように、パイプラインは出力ファイルが入力ファイルと異なることを確認します。
