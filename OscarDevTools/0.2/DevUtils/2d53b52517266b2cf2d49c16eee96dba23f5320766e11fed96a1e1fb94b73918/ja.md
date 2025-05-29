```
oscar_add_remotes(fork::String; <keyword arguments>)
oscar_add_remotes(pkgs::Array{String}, fork::String; <keyword arguments>)
```

`pkgs`内の各Oscarパッケージ（または`pkgs`が指定されていない場合は`dir`に存在するパッケージ）に対して、`https://github.com/fork/PackageName.jl`の新しいgitリモートを追加します。push-urlは`git@github.com:fork/PackageName.jl`に設定され、ssh経由でのプッシュを容易にします。

# 引数

  * `pkgs::Array{String}`: 操作対象のパッケージのリストで、`.jl`は省略してください。
  * `fork::String`: 新しいリモートのgithub組織/ユーザー
  * `dir="oscar-dev"`: 開発用サブディレクトリ。
