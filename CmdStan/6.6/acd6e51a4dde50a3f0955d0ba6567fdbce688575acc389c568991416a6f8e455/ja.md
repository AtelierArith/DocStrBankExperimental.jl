# stan

Stanモデルを実行します。

### メソッド

```julia
rc, sim, cnames = stan(
  model::Stanmodel, 
  data=Nothing, 
  ProjDir=pwd();
  init=Nothing,
  summary=true, 
  diagnostics=false, 
  CmdStanDir=CMDSTAN_HOME,
  file_run_log=true
)
```

### 必要な引数

```julia
* `model::Stanmodel`              : ?Methodを参照
```

### オプションの位置引数

```julia
* `data=Nothing`                  : 観測された入力データ辞書 
* `ProjDir=pwd()`                 : プロジェクト作業ディレクトリ
```

### キーワード引数

```julia
* `init=Nothing`                  : 初期パラメータ値辞書
* `summary=true`                  : CmdStanのstansummaryを使用して結果を表示
* `diagnostics=false`             : 診断ファイルを生成
* `CmdStanDir=CMDSTAN_HOME`       : cmdstanディレクトリの場所
* `file_run_log=true`             : 実行ログファイルを作成（falseの場合、ログをstdoutに書き込む）
* `file_make_log=true`            : makeログファイルを作成（falseの場合、ログをstdoutに書き込む）
```

`data`または`init`引数の型がAbstractStringの場合、これは既存の.Rファイルへのパス名として解釈されます。このファイルは、各チェーンの対応する.Rデータおよび/またはinitファイルにコピーされます。

### 戻り値

```julia
* `rc::Int`                       : stan()からの戻りコード、rc == 0はすべてが正常であることを示す
* `samples`                       : サンプル
* `cnames`                        : 変数名のベクター
```

### 例

```julia
# データなし、デフォルトのProjDirを使用（pwd）
stan(mymodel)
# デフォルトのProjDir（pwd）
stan(mymodel, mydata)
# ProjDirを指定
stan(mymodel, mydata, "~/myproject/")
# キーワード引数
stan(mymodel, mydata, "~/myproject/", diagnostics=true, summary=false)
# デフォルトのProjDir（pwd）を使用し、キーワード引数を指定
stan(mymodel, mydata, diagnostics=true, summary=false)
```

### 関連ヘルプ

```julia
?Stanmodel                         : StanModelを作成
```
