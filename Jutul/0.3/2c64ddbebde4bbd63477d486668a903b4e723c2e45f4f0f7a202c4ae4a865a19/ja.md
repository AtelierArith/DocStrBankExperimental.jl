```
pth = jutul_output_path(name = missing; subfolder = "jutul", basedir = missing, create = true)
```

出力のパスを取得します。最終的なパスは /basedir/<subfolder/name に見つかります。`subfolder=missing`の場合、パスは /basedir/name に設定されます。`name`は提供されていない場合、自動生成されます。

ディレクトリを作成しないようにするには、オプションの入力 `create = false` を渡します。デフォルトの出力ディレクトリをグローバルに設定するには、`ENV["JUTUL_OUTPUT_PATH"]` を希望する `basedir` に設定します。
