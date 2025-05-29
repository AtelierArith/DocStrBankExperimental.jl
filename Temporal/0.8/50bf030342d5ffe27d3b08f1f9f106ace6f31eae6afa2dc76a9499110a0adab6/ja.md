```
tswrite(x::TS,file::String;dlm::Char=',',header::Bool=true,eol::Char='\n')::Nothing
```

時系列データをテキストファイルに書き込みます。

# 引数

  * `x::TS`: ファイルに書き込む時系列オブジェクト
  * `file::String`: オブジェクトを書き込むファイルパス

オプション引数:

  * `dlm::Char=','`: 列を区切るために使用されるデリミタ
  * `header::Bool=true`: オブジェクトの `fields` メンバーを出力ファイルのヘッダー行として含めるかどうか
  * `eol::Char='\n'`: 行の終わりを指定するために使用される文字

# 例

```
X = TS(randn(252, 4))
tswrite(X, "data.csv")
```
