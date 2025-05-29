```
deploy_artifact_paths(dest::AbstractString, artifact_paths;
                      strategy::Symbol = :auto)
```

指定されたデプロイメント戦略を使用して、指定された宛先にアーティファクトをデプロイします。使用可能な戦略は3つあります: `:symlink`、`:hardlink`、および `:copy`。デフォルトでは、`deploy_artifact_paths()` は `:hardlink` が許可されているかどうかを確認し、許可されている場合はそれを使用します。そうでない場合は、最も安全な `:copy` にフォールバックします。これは、実行可能ファイルが自分自身に対して相対パスで依存ライブラリを見つけるために `RPATH` を使用することを期待している場合に最適です。`:hardlink` が機能しないと確信している場合は、ファイルが物理的に隣接している必要がない場合に `:symlink` を強制的に使用することができます。
