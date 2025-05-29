```
savenodeinfo(net,filename)
```

ノードに関する情報をファイル *filename* に保存します。

ファイルはテキストモードで書き込まれます。書き込まれる各行は1つのノードに対応しています。行の形式は次の通りです。

```
NODEID STATE INDEGREE OUTDEGREE IN-NEIGHBORS OUT-NEIGBORS
```

ここで、NODEID はノードのID、STATE はノードの状態、INDEGREE はノードが宛先であるリンクの数、OUTDEGREE はノードがソースであるリンクの数、IN-NEIGHBORS は焦点ノードが受け取るすべてのノードのリスト、OUTNEIGHBORS は焦点ノードが送信するすべてのノードのIDのリストです。すべての要素はスペースで区切られています。行は改行 '\n' で終了します。

[linklist](#Fastnet.linklist) も参照してください。
