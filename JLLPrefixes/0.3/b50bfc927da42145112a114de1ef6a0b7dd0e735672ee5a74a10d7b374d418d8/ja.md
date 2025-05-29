```
collect_artifact_metas(dependencies::Vector;
                       platform = HostPlatform(),
                       verbose = false)
```

指定された `platform` のために (再帰的に) JLL 依存関係のアーティファクトメタデータを収集します。 各 (再帰的な) 依存関係をそのアーティファクトメタのセットにマッピングする辞書を返し、それを変換したりフラット化して、`symlink_artifact_paths()` や `copy_artifact_paths()` などの他のツールに渡すことができます。

依存関係は `PkgSpec` として指定できるため、`Pkg.add()` と同様にパッケージの特定のバージョンを要求することが可能です。

`platform` キーワード引数は、外国のプラットフォームや異なる Julia バージョンのためにアーティファクトを収集することを可能にします。 これは、標準ライブラリであり、したがって Julia バージョンに基づいて単一のバージョンにロックされているパッケージに特に便利です。
