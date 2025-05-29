```
TAPService(baseurl, [format="VOTABLE/TD"])
TAPService(service::Symbol)
```

仮想天文台テーブルアクセスプロトコル（TAP）に従ったサービスのハンドラーであり、IVOAによって[定義](https://www.ivoa.net/documents/TAP/)されています。`TAPService`のインスタンスは、サービスのベースURLまたは既知のサービスに対応するシンボル（`:cadc`, `:gaia`, `:ned`, `:simbad`, `:vizier`）を渡すことで作成できます。

`TAPService`は、クエリ実行を主な機能とする`DBInterface`インターフェースに従うことを目指しています：`execute(tap, query::String)`。

`TAPService`のクエリは`HTTP.request`を使用します。`HTTP.request`のキーワード引数は、`VirtualObservator.HTTP_REQUEST_OPTIONS`の`Dict`で指定できます。詳細については、`HTTP_REQUEST_OPTIONS`および`HTTP.request`のドキュメントを参照してください。
