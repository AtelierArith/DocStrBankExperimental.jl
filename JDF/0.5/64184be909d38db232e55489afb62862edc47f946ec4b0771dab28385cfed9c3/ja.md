```
jdf"path/to/JDFfile.jdf"

JDFFile("path/to/JDFfile.jdf")
```

JDFファイルを定義します。`names`と`size`を適用できます。

## 例

using JDF, DataFrames df = DataFrame(a = 1:3, b = 1:3) savejdf(df, "plsdel.jdf")

names(jdf"plsdel.jdf") # [:a, :b] ncol(jdf"plsdel.jdf") # 2 size(jdf"plsdel.jdf") # (2, 3)

size(jdf"plsdel.jdf", 1) # (2, 3)

size(jdf"plsdel.jdf", 1) # (2, 3)

# クリーンアップ

rm("plsdel.jdf", force = true, recursive = true)
