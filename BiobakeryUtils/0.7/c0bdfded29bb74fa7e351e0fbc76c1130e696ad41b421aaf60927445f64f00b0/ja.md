```
metaphlan(inputfile, outputfile; kwargs...)
```

`inputfile`に対して`metaphlan`コマンドラインツールを実行し、`outputfile`を作成します。`metaphlan`がインストールされ、`PATH`でアクセス可能である必要があります（[Getting Started](@ref)を参照）。

`metaphlan`オプションはキーワード引数を介して渡すことができます。たとえば、コマンドラインで次のように実行する場合：

```sh
$ metaphlan some.fastq.gz output/some_profile.tsv --input_type fastq --nproc 8
```

この関数を使用すると、次のように書きます：

```julia
metaphlan("some.fastq.gz", "output/some_profile.tsv"; input_type="fastq", nproc=8)
```

注意：`input_type`キーワードは必須です。

環境変数`"METAPHLAN_BOWTIE2_DB"`を設定して、マーカー遺伝子データベースがインストールされる場所を指定するか、`bowtie2db = "some/path"`をキーワード引数として渡してください。
