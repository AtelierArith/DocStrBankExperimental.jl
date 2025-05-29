```
savelinklist(net,filename)
```

ネットワーク *net* のリンクリストをファイル *filename* に保存します。

ファイルはテキストモードで書き込まれます。書き込まれる各行は1つのリンクに対応しています。行の形式は次の通りです。

```
LINKID SOURCE DESTINATION
```

ここで、LINKID はそれぞれのリンク、SOURCE はソースノードのノードID、DESTINATION はデスティネーションノードのノードIDです。要素はスペースで区切られています。行は改行 '\n' で終了します。

詳細は [linklist](#Fastnet.linklist) を参照してください。
