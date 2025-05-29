```
storage(storer::DataStorage, as::Type; write::Bool=false)
```

`storer`を`as`の形式で取得し、（`write`に応じて）読み取りまたは書き込みに適したものにします。

デフォルトでは、これは単に`getstorage`または`putstorage`（`write=true`のとき）を呼び出します。

これは全体のデータフローのこのコンポーネントを実行します：

```
Storage ◀────▶ Data
```
