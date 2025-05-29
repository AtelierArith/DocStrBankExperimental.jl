```
humann(inputfile, output[, flags]; kwargs...)
```

`inputfile`に対して`humann`コマンドラインツールを実行し、出力を`output`に保存します。`humann`がインストールされ、`PATH`でアクセス可能である必要があります（[Getting Started](@ref)を参照）。

`humann`フラグオプション（パラメータを持たないもの）は配列で渡すことができ、他のオプションはキーワード引数で渡すことができます。たとえば、コマンドラインで次のように実行する場合：

```sh
$ humann -i $INPUTFILE -o $OUTPUT --bypass-tranlated-search --input-format fastq.gz --output-format biom
```

この関数を使用すると、次のように書きます：

```julia
humann(INTPUTFILE, OUTPUT, ["bypass_translated_search"]; input_formal="fastq.gz", output_format="biom")
```
