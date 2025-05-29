ヘッダーキーワードまたはCOMMENTエントリに関連付けられたコメントにアクセスするためのインデックス。

例：

```julia
img = AstroImage(randn(10,10))
img["ABC"] = 1
img["ABC", Comment] = "このキーを説明するコメント"

push!(img, Comment, "このファイルの目的はコメントを示すことです")
img[Comment] # ["このファイルの目的はコメントを示すことです"]
```
