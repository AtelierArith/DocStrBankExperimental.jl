```
tess_run_pipeline(
    func::Function,
    pipe::TessPipeline,
    title::AbstractString = ""
)::Bool
```

パイプラインを一連の画像に対して実行します。

**引数:**

| T   | 名前    | デフォルト | 説明                 |
|:--- |:----- |:----- |:------------------ |
| R   | func  |       | 画像に対して呼び出すコールバック。  |
| R   | pipe  |       | 実行するパイプライン。        |
| O   | title | `""`  | ドキュメントのオプションのタイトル。 |

**詳細:**

これは `TessPipeline` オブジェクトの主要な関数です。このメソッドは、複数の画像からの出力を単一のドキュメント（または異なるタイプの複数のドキュメント）に結合するために使用されます。

関数に渡される引数は、次の形式のメソッドです：

```
function add(Pix, Integer)::Bool
```

クライアントは、このメソッドを画像と画像のインチあたりのピクセル数で呼び出します。画像は即座に処理され、パイプラインの出力に追加されます。

コールバックが false を返すと、`tess_run_pipeline()` は `false` を返します。ブール値を返さないか、`true` を返す場合、`tess_run_pipeline()` は他にエラーがないと仮定して `true` を返します。

このメソッドは「一度だけ」使用できます。呼び出された後は、再利用したい場合は新しい出力をパイプラインに追加する必要があります [`TessPipeline`](@ref) オブジェクト。

**例:**

```jldoctest
using Tesseract

# 読み込むページを生成します。
write("page01.tiff", sample_tiff())
write("page02.tiff", sample_tiff())
write("page03.tiff", sample_tiff())

download_languages() # データファイルがあることを確認します。

instance = TessInst()
pipeline = TessPipeline(instance)

book = tess_pipeline_text(pipeline)

tess_run_pipeline(pipeline, "My First Book") do add
    add(pix_read("page01.tiff"), 72)
    add(pix_read("page02.tiff"), 72)
    add(pix_read("page03.tiff"), 72)
end

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
