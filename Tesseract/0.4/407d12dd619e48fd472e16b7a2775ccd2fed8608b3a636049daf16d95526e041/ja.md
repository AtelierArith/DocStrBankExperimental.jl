```
tess_run_pipeline(
    pipe::TessPipeline,
    filename::AbstractString;
    retryConfig::AbstractString = "",
    timeout::Integer = Int32(0)
)::Bool
```

画像を処理するためのリストを含むファイルまたは複数の画像を含むTIFFファイルに対してパイプラインを実行します。プロセスが失敗した場合は`false`を返します。

**引数:**

| T   | 名前          | デフォルト      | 説明                        |
|:--- |:----------- |:---------- |:------------------------- |
| R   | pipe        |            | 実行するパイプラインです。             |
| R   | filename    |            | 読み込むファイルの名前です。            |
| K   | retryConfig | `""`       | 画像を処理できない場合に読み込む設定ファイルです。 |
| K   | timeout     | `Int32(0)` | ページごとに費やす最大時間（ミリ秒）です。     |

**詳細:**

このメソッドは`tess_run_pipeline`関数の簡略版を提供します。これは、追加の入力なしでファイルのリストまたは単一のTIFFファイルを処理するためにTesseractライブラリによって公開されたメソッドを使用します。

このメソッドは「一度」だけ使用できます。呼び出された後、[`TessPipeline`](@ref)オブジェクトを再利用したい場合は、新しい出力をパイプラインに追加する必要があります。

**例:**

処理する画像のリストを含むファイルを提供する:

```jldoctest
using Tesseract
using Suppressor

# 読み込むページを生成します。
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # データファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

book = tess_pipeline_text(pipeline)

# 処理するファイルを含むテキストファイルを作成します。
open("pages.lst", create = true, write = true) do io
    println(io, "page01.tiff")
    println(io, "page02.tiff")
    println(io, "page03.tiff")
end

@suppress tess_run_pipeline(pipeline, "pages.lst")

for line in split(book[], "\n")[1:10]
    println(line)
end

# 出力

No one would have believed in the last years of the

the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
```

複数ページのTIFFを使用する:

```jldoctest
using Tesseract
using Suppressor

# 読み込むページを生成します。
pix_write_tiff("book.tiff", sample_pix())
pix_write_tiff("book.tiff", sample_pix(); append = true)
pix_write_tiff("book.tiff", sample_pix(); append = true)

download_languages() # データファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

book = tess_pipeline_text(pipeline)

@suppress tess_run_pipeline(pipeline, "book.tiff")

for line in split(book[], "\n")[1:10]
    println(line)
end

# 出力

No one would have believed in the last years of the

the nineteenth century that this world was being watched
watched keenly and closely by intelligences greater than
than man’s and yet as mortal as his own; that as men busied
busied themselves about their various concerns they were
were scrutinised and studied, perhaps almost as narrowly as
as a man with a microscope might scrutinise the transient
transient creatures that swarm and multiply in a drop of
```

参照: [`TessPipeline`](@ref), [`tess_pipeline_text`](@ref)
