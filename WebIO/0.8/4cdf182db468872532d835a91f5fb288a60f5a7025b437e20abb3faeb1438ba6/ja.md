```
Asset(url)
Asset(name, url)
Asset(name => url)
Asset(filetype, name, url)
```

WebIOによってロード可能なブラウザアセット。

`url`パラメータは、リモートURLまたはローカルファイルパス（AssetRegistry.jlを介して提供されます）のいずれかである可能性があります。以下のすべては有効な`url`値です。

  * `https://unpkg.com/react@16/umd/react.development.js`
  * `//unpkg.com/react@16/umd/react.development.js`
  * `./path/to/foo.js`

デフォルトでは、ファイルタイプは指定されたurlの拡張子として推測されます（現在サポートされているのは`"js"`、`"css"`、および`"html"`のみ）が、非標準の拡張子が使用されている場合は指定することができます。
