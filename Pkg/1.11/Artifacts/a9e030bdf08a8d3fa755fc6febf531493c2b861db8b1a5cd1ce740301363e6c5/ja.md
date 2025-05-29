```
create_artifact(f::Function)
```

新しいアーティファクトを作成するために `f(artifact_path)` を実行し、その結果をハッシュ化してアーティファクトストア（通常のインストールでは `~/.julia/artifacts`）に移動します。このアーティファクトの識別ツリーハッシュを返します。
