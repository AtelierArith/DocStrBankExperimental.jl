```
collect_artifact_paths(dependencies::Vector;
                       platform = HostPlatform(),
                       verbose = false)
```

`collect_artifact_metas()`の便利なラッパーで、`meta`オブジェクトを剥がし、依存関係ツリーを辿り、`dependencies`内の各パッケージをフラットなアーティファクトパスディレクトリのベクトルにマッピングする辞書を返します。ツリーをさらにフラットにして単一のベクトルにするには、`flatten_artifact_paths()`を使用してください。
