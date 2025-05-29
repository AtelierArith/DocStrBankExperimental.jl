```
get_citations(; only_direct=false, filename="julia_citations.bib")
```

この関数は、現在のアクティブな環境の依存関係に対応するCITATION.bibファイルから収集したすべての引用を含む.bibファイルを作成します。ファイル名を変更するには`filename`を使用します。直接の依存関係のみを含めるには`only_direct=true`を使用します。`badge = true`を使用すると、`Citation.bib`ファイルがないパッケージから、DOIバッジを持つ引用を取得できます。
