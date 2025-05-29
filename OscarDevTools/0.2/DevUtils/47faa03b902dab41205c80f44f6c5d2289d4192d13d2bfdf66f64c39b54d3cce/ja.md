```
oscar_branch(branch::AbstractString; <キーワード引数>)
oscar_branch(pkgs::Array{String}, branch::AbstractString; <キーワード引数>)
```

`pkgs`に指定された各Oscarパッケージに対して、現在の開発ディレクトリである`dir`の下の作業コピーに`start`を起点とする`branch`という名前の新しいローカルブランチを作成します。`pkgs`配列が指定されていない場合は、`dir`のすべてのサブディレクトリで実行されます。

ディレクトリ`dir`が存在せず、`pkgs`が指定されている場合は、最初に[`oscar_develop`](@ref)を呼び出してすべての`pkgs`をチェックアウトします。

# 引数

  * `pkgs::Array{String}`: 操作対象のパッケージのリストで、`.jl`は省略してください。
  * `branch::String`: 新しいブランチ名。
  * `dir="oscar-dev"`: 開発サブディレクトリ。
  * `start="origin/master"`: ブランチの起点、各ディレクトリの現在のHEADには`HEAD`を使用します。

```
