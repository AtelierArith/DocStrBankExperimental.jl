```
tabletype(d::DTable)
```

基になるテーブルパーティションのタイプを提供します。利用可能な場合はキャッシュされたtabletypeを使用します。

tabletypeを取得できない場合のデフォルトの返り値は`NamedTuple`です。
