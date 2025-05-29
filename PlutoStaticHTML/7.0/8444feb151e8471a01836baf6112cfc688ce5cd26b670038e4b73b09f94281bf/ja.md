```
BuildOptions(
    dir::AbstractString;
    write_files::Bool=true,
    previous_dir::Union{Nothing,AbstractString}=nothing,
    output_format::Union{OutputFormat,Vector{OutputFormat}}=html_output,
    add_documenter_css::Bool=true,
    use_distributed::Bool=true,
    compiler_options::Union{Nothing,CompilerOptions}=nothing,
    max_concurrent_runs::Int=4
)
```

引数:

  * `dir`:   Plutoノートブックが保存されているディレクトリ。
  * `write_files`:   `joinpath(dir, "$file.html")`にファイルを書き込む。
  * `previous_dir::Union{Nothing,AbstractString}=Nothing`:   前回の実行からの出力をキャッシュとして使用して実行時間を短縮する。   キャッシュを使用するには、前回の実行からのHTMLまたはMarkdownファイルを含むディレクトリ`previous_dir::AbstractString`を指定する必要があります。   特に、ファイルは`joinpath(previous_dir, "$file.html")`にあることが期待されます。   前回の実行からの出力は、より大きなHTMLまたはMarkdownファイルに埋め込まれている可能性があります。   このパッケージは、ファイルの全内容から元の出力を抽出します。   デフォルトでは、キャッシュは無効になっています。
  * `output_format`:   出力をどのファイルに書き込むか。   デフォルトでは、これは`html_output::OutputFormat`であり、HTMLメソッドの出力は純粋なHTMLです。   Franklin、Documenter、またはPDFファイルを生成するには、それぞれ`franklin_output`、`documenter_output`、または`pdf_output`を使用します。   `BuildOptions.write_files == true`で`output_format == franklin_output`または`output_format == documenter_output`の場合、出力ファイルは".md"拡張子を持ち、".html"ではありません。   `BuildOptions.write_files == true`で`output_format == pdf_output`の場合、".tex"と".pdf"拡張子の2つの出力ファイルが作成されます。
  * `add_documenter_css`:   `documenter_output=true`のときにHTMLにCSSスタイルを追加するかどうか。
  * `use_distributed`:   異なるプロセスでノートブックをビルドするかどうか。   デフォルトでは、これはPlutoと同様に有効であり、ノートブックは並行してビルドされます。   異なるプロセスの利点は、互いにより独立していることです。   残念ながら、欠点は、各プロセスでコンパイルが行われなければならないことです。   このオプションを`false`に設定すると、すべてのノートブックが同じプロセスで逐次的にビルドされ、再コンパイルを回避します。   これは、ノートブックの内容に依存するGitHub Runnersのように、利用可能なスレッドが少ない状況ではより迅速である可能性があります。   `use_distributed=false`は、Plutoの組み込みパッケージマネージャーでは**機能しません**ので注意してください。
  * `compiler_options`:   Plutoに渡す`Pluto.Configuration.CompilerOptions`。   これは、例えば、`PackageCompiler.jl`からカスタムシステムイメージを渡すのに役立ちます。
  * `max_concurrent_runs`:   `use_distributed=true`のときに同時に評価するノートブックの最大数。   各ノートブックは異なるプロセスで開始され、複数のスレッドを開始できるため、この数を高く設定しすぎないでください。そうしないと、CPUがタスクの切り替えに忙しくなり、生産的な作業ができなくなる可能性があります。
