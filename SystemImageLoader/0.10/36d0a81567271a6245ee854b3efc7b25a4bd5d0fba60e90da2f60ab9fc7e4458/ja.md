ユーザーがローカルにインストールしたいアーティファクトを選択するために実行できるインタラクティブなアーティファクトインストーラーを定義します。

```julia
module MySystemImageProvider

using SystemImageLoader

const install = @ArtifactInstaller "../Artifacts.toml"

end
```

ユーザーは、インストールのために利用可能なイメージを選択するインタラクティブなプロンプトを取得するために `MySystemImageProvider.install()` を呼び出すか、非インタラクティブな使用のために `MySystemImageProvider.install("NameOfImage")` を実行することができます。
