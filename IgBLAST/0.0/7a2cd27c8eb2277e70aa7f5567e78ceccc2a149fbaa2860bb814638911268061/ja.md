```
IgBLAST
```

免疫グロブリン（Ig）およびT細胞受容体（TCR）配列に対してIgBLAST分析を実行するためのJuliaパッケージです。

このパッケージは、IgBLASTnおよびIgBLASTpの両方のバリアントをサポートし、IgBLASTをインストールして実行するための便利なインターフェースを提供します。IgBLASTバイナリのインストール、入力ファイルの準備、分析の実行、進捗の監視を行います。

# エクスポート

  * `install_igblast`: IgBLASTバイナリをインストールするための関数
  * `run_igblast`: IgBLAST分析を実行するためのメイン関数
  * `is_igblast_installed`: IgBLASTがインストールされているかどうかを確認するための関数
  * `IgBLASTn`: IgBLASTのヌクレオチドバージョンを表す型
  * `IgBLASTp`: IgBLASTのタンパク質バージョンを表す型

# 例

```julia
using IgBLAST

# まだインストールされていない場合はIgBLASTをインストール
install_igblast()

# IgBLASTn分析を実行
run_igblast(
    IgBLASTn,
    "query.fasta",
    "V.fasta",
    "D.fasta",
    "J.fasta",
    "auxiliary.txt",
    "output.txt",
    additional_params = Dict("organism" => "human", "domain_system" => "imgt")
)
```
