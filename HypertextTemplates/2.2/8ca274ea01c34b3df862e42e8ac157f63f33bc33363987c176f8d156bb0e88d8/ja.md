```
@deftag macro name end
@deftag name
```

与えられた要素またはコンポーネントのマクロバージョンを `name` と呼ばれる名前で作成します。これは、与えられた `name` で `@<` マクロを呼び出すためのショートハンドであり、ソース情報をレンダラーに正しく渡すことができます。`macro` バリアントは、LSP が定義の位置を正しく推測できるようにしますが、プレーンシンボルバリアントではそうではありません。
