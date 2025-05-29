```
verify_artifact(hash::SHA1; honor_overrides::Bool=false)
```

指定されたアーティファクト（SHA1 gitツリーハッシュによって識別される）がディスクにインストールされており、その整合性が保持されていることを確認します。指定されたアーティファクトがオーバーライドされている場合、`honor_overrides`が`true`に設定されていない限り、検証をスキップします。
