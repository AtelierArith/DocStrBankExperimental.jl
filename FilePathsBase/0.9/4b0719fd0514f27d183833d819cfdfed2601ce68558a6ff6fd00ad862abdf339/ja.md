```
cp(src::AbstractPath, dst::AbstractPath; force=false, follow_symlinks=false)
```

`src`から`dst`にファイルまたはディレクトリをコピーします。既存の`dst`は`force=true`の場合のみ上書きされます。パスの種類がシンボリックリンクをサポートしている場合、`follow_symlinks=true`はシンボリックリンクの内容を宛先にコピーします。
