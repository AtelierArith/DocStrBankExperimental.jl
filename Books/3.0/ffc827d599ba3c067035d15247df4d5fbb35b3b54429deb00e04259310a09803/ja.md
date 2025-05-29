<h1 align="center">Books.jl</h1>

<h3 align="center">   Juliaで本を作成する </h3>

<p align="center">     <a href="https://github.com/JuliaBooks/Books.jl/actions?query=workflow%3ACI+branch%3Amain">         <img src="https://github.com/JuliaBooks/Books.jl/workflows/CI/badge.svg" alt="CI">     </a>     <a href="https://huijzer.xyz/Books.jl/">         <img src="https://img.shields.io/badge/Documentation-main-blue" alt="Documentation">     </a>     <a href="https://github.com/invenia/BlueStyle">         <img src="https://img.shields.io/badge/Code%20Style-Blue-4495d1.svg" alt="Code Style Blue">     </a> </p>

要するに、このパッケージは埋め込まれたJulia出力を持つ本（またはレポートやダッシュボード）を生成することを目的としています。Pandocを介して、このパッケージはウェブサイトをライブサーブし、ウェブサイトやPDFを含むさまざまな出力を構築できます。DataFramesやプロットなどの多くの標準出力タイプに対して、このパッケージはコードを実行し、出力ドキュメントへの適切な埋め込みを自動的に処理し、適切なキャプションやラベルを推測しようとします。また、ライブサーバーを介して作業することも可能で、数秒以内に変更を表示します。

このパッケージは以下を前提としています：

  * ユーザーが2つのREPLを管理することに慣れていること、
  * ユーザーがJuliaコードを実行し、その出力を本に埋め込みたいこと、
  * 本（ウェブサイトとPDF）がCIを介して構築されること、
  * Markdownのセクションとサブセクション（レベル2）が番号付けされ、HTMLメニューにリストされること。

セクションの番号付けが常に前提とされる理由は、本を印刷できるようにするためです。セクション番号がないと、本の他の部分を参照するのが難しくなります。

番号付きセクションではなく、リンクのあるより動的なウェブサイトを希望する場合は、[Franklin.jl](https://github.com/tlienart/Franklin.jl)や私の[Plutoを使ったFranklinのテンプレートリポジトリ](https://github.com/rikhuijzer/JuliaTutorialsTemplate)をチェックしてください。番号付きセクションのある本ではなく、小さなレポートが必要な場合は、[Weave.jl](https://github.com/JunoLab/Weave.jl)があなたの問題により適しているかもしれません。

このパッケージは[Julia Data Science book](https://juliadatascience.io)を作成するために使用されます。

## 使用法

このパッケージをインストールするには（MacOS/LinuxのJulia 1.6/1.7/1.8）、次のコマンドを使用します。

```
pkg> add Books
```

詳細については、[ドキュメント](https://huijzer.xyz/Books.jl/)を参照してください。

### Windows

現在、このパッケージは（おそらく）Windowsでは動作しません。これは、最大ファイルパスの長さの違いによるもののようです。これを修正するためにもう少し調査する必要がありますが、私にとっては優先事項ではありません。

### ヘルプを得る

このパッケージを使用しているときに問題が発生した場合は、GitHubでここに問題をオープンするか、[この]( https://discourse.julialang.org/new-topic?title=Books.jl%20-%20Your%20question%20here&category=usage&tags=Books&body=You%20can%20write%20your%20question%20in%20this%20space. )リンクをクリックしてDiscourseで質問してください。短い質問の場合は、[https://julialang.zulipchat.com/](https://julialang.zulipchat.com/)で私にPMを送ってください。
