```
oscar_develop(pkgs::Array{String}; <キーワード引数>)
oscar_develop(pkgs::Dict{String,Any}; <キーワード引数>)
```

`pkgs`に指定された各Oscarパッケージについて、`dir`に新しいチェックアウトを作成し、*既存の*アップストリームブランチ`branch`（または`master`にフォールバック）用の新しいトラッキングブランチを作成しようとします。

*注:* 新しい機能のために新しいブランチを作成するには、[`oscar_branch`](@ref)を使用してください。

`fork`が指定されている場合、ブランチは`https://github.com/fork/pkg.jl`で検索され、`origin`に加えて自動的に2番目のリモートが作成されます。`origin`は常にメインリポジトリを指します。

プッシュURLは`git@github.com:org-name/PackageName.jl`に設定され、ssh経由でのプッシュを容易にします（`origin`とオプションの`fork`の両方に対して）。

これらのパッケージチェックアウトは、`dir/project`に新しいjuliaプロジェクトに追加（dev'd）され、次のようにjuliaを実行することで使用できます：

```
julia --project=dir/project
```

# 引数

  * `pkgs`: 操作するパッケージのリストで、`.jl`は省略してください。
  * `branch::String="master"`: チェックアウト用のブランチ。
  * `dir="oscar-dev"`: 開発用サブディレクトリ。
  * `fork=nothing`: すべてのパッケージのブランチ検索用のgithub組織/ユーザー。
  * `active_repo=nothing`: CIでそのパッケージの既存のチェックアウトを再利用するために使用され、github変数`$GITHUB_REPOSITORY`に対応します。
  * `merge=false`: CI用: `true`の場合、各チェックアウトプロジェクトに最新の`origin/master`をマージしようとします。文字列が指定された場合は、他のブランチもマージします。これはマージコミットを作成しないことに注意してください（`--no-commit`に似ています）。

各パッケージ名には、オプションでブランチ名とフォークURLを含めることができます：

  * `PackageName#somebranch`は、デフォルトのアップストリームから`somebranch`をチェックアウトします。
  * `PackageName#https://github.com/myfork/PackageName.jl#otherbranch`は、このパッケージに対して`myfork`ユーザーを使用します。

パッケージ名とブランチは、`PackageName.jl`を`[forkurl#]branchname`にマッピングする辞書としても指定できます。

# 例

```julia-repl
julia> oscar_develop(["Oscar","Polymake"]; branch="some_feature")
```

```julia-repl
julia> oscar_develop(["Oscar","Singular#more_rings"]; dir="dev_more_rings")
```
