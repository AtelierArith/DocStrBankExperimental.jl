```
@testcase [option=val ...] <name> begin ... end
@testcase [option=val ...] <name> for x in fx1, (y, z) in fx2 ... end
```

テストケースオブジェクトを作成し、現在のテストグループに追加します。

利用可能なオプション：

`tags :: Array{Symbol, 1}`: テストケースのタグのリスト。
