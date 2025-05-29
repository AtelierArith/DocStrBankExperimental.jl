```
UA_WRITEMASK(; accesslevel = false, arraydimensions = false,
        browsename = false, containsnoloops = false, datatype = false,
        description = false, displayname = false, eventnotifier = false,
        executable = false, historizing = false, inversename = false,
        isabstract = false, minimumsamplinginterval = false, nodeclass = false,
        nodeid = false, symmetric = false, useraccesslevel = false, 
        userexecutable = false, userwritemask = false, valuerank = false,
        writemask = false, valueforvariabletype = false)::UInt32
```

は、ノードのどの属性が書き込み可能であるかを表す `UInt32` 数値を計算します。キーワードの意味はここで説明されています: [OPC Foundation website](https://reference.opcfoundation.org/Core/Part3/v105/docs/8.60)

特定のノードタイプが属性をサポートしていない場合、対応するキーワードは false に設定する必要があります。*これは現在自動的には強制されていません。*
