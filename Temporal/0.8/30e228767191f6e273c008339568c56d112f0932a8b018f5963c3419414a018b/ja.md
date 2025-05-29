```
tsread(file::String;dlm::Char=',',header::Bool=true,eol::Char='\n',indextype::Type=Date,format::String="yyyy-mm-dd")::TS
```

テキストファイルからTSオブジェクトに内容を読み込みます。

# 引数

  * `file::String`: 入力ファイルへのパス

オプション引数:

  * `dlm::Char=','`: 列を区切るために使用される区切り文字
  * `header::Bool=true`: ヘッダー行が存在するかどうか
  * `eol::Char='\n'`: 行の終わりを指定するために使用される文字
  * `indextype::Type=Date`: DateTimeまたはDate
  * `format::String="yyyy-mm-dd"`: インデックスを解析するために使用されるフォーマット

# 例

```
X = tsread("data.csv")
```
