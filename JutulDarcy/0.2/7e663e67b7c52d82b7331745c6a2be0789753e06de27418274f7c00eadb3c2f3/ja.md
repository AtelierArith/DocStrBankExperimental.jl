```
generate_jutuldarcy_examples(
    pth = pwd(),
    name = "jutuldarcy_examples";
    makie = nothing,
    project = true,
    print = true,
    force = false
)
```

`pth`内のすべてのJutulDarcyの例をサブフォルダ`jutuldarcy_examples`にコピーします。フォルダがすでに存在する場合はエラーが発生しますが、`force=true`の場合はフォルダが上書きされ、既存の内容は永久に失われます。`project=true`の場合、例を実行するために必要なすべての依存関係を含む、ドキュメントビルドシステムと同じ依存関係を持つ`Project.toml`ファイルが生成されます。

`makie`引数は、例の中のGLMakieへの呼び出しを、`String`で指定された別のバックエンドに置き換えることを可能にします。置き換えが有効なMakieバックエンドの名前であるかどうかのチェックは行われません。
