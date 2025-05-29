```
kneaddata(inputfile, outputfile; kwargs...)
```

`inputfile`に対して`kneaddata`コマンドラインツールを実行し、`outputfile`を作成します。`kneaddata`がインストールされ、`PATH`でアクセス可能である必要があります（詳細は[Getting Started](@ref)を参照）。

`kneaddata`のオプションはキーワード引数を介して渡すことができます。たとえば、コマンドラインで次のように実行する場合：

```sh
$ kneaddata -i some.fastq.gz -o test --n 8 --bypass-trim
```

この関数を使用する場合は、次のように記述します：

```julia
kneaddata("some.fastq.gz", "test"; n = 8, bypass_trim=true)
```

複数のデータベースを渡すには、`reference_db`引数にパスの配列を渡します。

`trimmomatic`（`kneaddata`の依存関係）のCondaインストールは、初期設定では正しく動作しません。コマンドラインのcondaを使用して`kneaddata`をインストールした場合（`Conda.jl`ではなく）、`trimmomatic = /path/to/trimmomatic`を使用してください。ここで、`/path/to/trimmomatic`は`/home/username/miniconda3/envs/biobakery3/share/trimmomatic`のようなものです。`BiobakeryUtils.install_deps()`を使用した場合は、これを心配する必要はありません。
