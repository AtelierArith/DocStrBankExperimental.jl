```
delimited(infile::String; delim::Union{Char,String,Regex} = "auto", digits::Int64 = 3, silent::Bool = false)
```

ポップデータオブジェクトとしてメモリに区切り文字付きファイルを読み込みます。

### 引数

  * `infile` : ファイルへのパス

### キーワード引数

  * `delim` : 区切り文字。デフォルトでは `CSV.File` の自動解析を使用します。
  * `digits` : 各アレルを示す桁数（デフォルト: `3`）
  * `silent`   : インポート中にファイル情報を表示するかどうか（デフォルト: `true`）
  * `allow_monomorphic::Bool` : データセットに単型ロキを保持するかどうか（デフォルト: `false`）

### ファイルフォーマット:

  * 最初の行は列名です（名前は重要ではありません）
  * 列はこの順序でなければなりません：

    1. サンプル名
    2. 集団名
    3. 経度
    4. 緯度
    5. locus_1 ジェノタイプ
    6. locus_2 ジェノタイプ
    7. その他...

#### 欠損データ

##### ジェノタイプ

欠損ジェノタイプは、すべてゼロの `000000`、空白、またはマイナス9 `-9` としてフォーマットできます。

##### 位置データ

サンプルの位置データが欠損している場合（問題ありません！）、値が空白であることを確認してください。そうしないと、転写エラーが発生します！（以下の例の行3を見てください）

## 例

```
lizardsCA = delimited("CA_lizards.csv", digits = 3);
```

### フォーマット例:

```
name,population,long,lat,Locus1,Locus2,Locus3 
sierra_01,mountain,11.11,-22.22,001001,-9,001001
sierra_02,mountain,11.12,-22.21,001001,001001,001002
snbarb_01,coast,,,001001,000000,001002
snbarb_02,coast,11.14,-22.24,001001,001001,001001
snbarb_03,coast,11.15,,001002,001001,001001
```
