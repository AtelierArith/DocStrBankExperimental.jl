```
archive_artifact(hash::SHA1, tarball_path::String; honor_overrides::Bool=false)
```

アーティファクトを `tarball_path` に保存された tarball にアーカイブし、結果の tarball の SHA256 を16進数の文字列として返します。アーティファクトが存在しない場合はエラーをスローします。アーティファクトがオーバーライドされている場合、`honor_overrides` が設定されていない限りエラーをスローします。
