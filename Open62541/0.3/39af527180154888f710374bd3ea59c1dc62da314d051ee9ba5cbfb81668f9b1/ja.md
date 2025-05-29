```
UA_ACCESSLEVEL(; read = false, write = false, historyread = false, 
        historywrite = false, semanticchange = false, statuswrite = false, 
        timestampwrite = false)::UInt8
```

は、変数の値にどのようにアクセスできるかを表す `UInt8` 数値を計算します。デフォルトはすべての操作を禁止することです。キーワードの意味はここで説明されています: [OPC Foundation website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.57)
