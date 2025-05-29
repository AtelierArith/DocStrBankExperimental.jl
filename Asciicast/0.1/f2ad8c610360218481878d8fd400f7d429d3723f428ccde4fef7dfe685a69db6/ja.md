```
cast_document(input_path, output_path=input_path; format="gfm+attributes")
```

入力ドキュメント内の各 `julia {cast="true"}` コードブロックに対して、そのコードをREPLで実行しているgifを生成し、`joinpath(dirname(output_path), "assets")` に保存し、コードブロックの後に画像として挿入し、結果のドキュメントを `output_path` に書き込みます。

デフォルトの `format` はGitHubフレーバーのマークダウンです。代替のpandocサポート形式を選択するには、`format` キーワード引数を指定してください（詳細は [https://pandoc.org/MANUAL.html#general-options](https://pandoc.org/MANUAL.html#general-options) を参照）。これはGitHubフレーバーのマークダウンでのみテストされていますが、理論的には任意のpandoc形式で動作するはずです。

生成されたgifの数を返します。

!!! warning
    この関数は、ドキュメントをpandocを使用して解析し、pandoc ASTを通じてラウンドトリップすることに依存しています。これにより、ドキュメントに予期しない変更が加わる可能性があります。

    この関数を実行する前にドキュメントをソース管理にチェックインするか、入力パスとは異なる `output_path` を指定して結果を評価することをお勧めします。

