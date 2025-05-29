```
Template(; kwargs...)
```

パッケージを生成するために使用される設定。

## キーワード引数

### ユーザーオプション

  * `user::AbstractString=""`: GitHub（または他のコードホスティングサービス）のユーザー名。デフォルト値はグローバルGit設定（`github.user`）から取得されます。値が取得できない場合、この値を使用する多くのプラグインが機能しなくなります。
  * `authors::Union{AbstractString, Vector{<:AbstractString}}="terasakisatoshi <terasakisatoshi.math@gmail.com> and contributors"`: パッケージの著者。`user`と同様に、デフォルト値はグローバルGit設定（`user.name`および`user.email`）から取得されます。

### パッケージオプション

  * `dir::AbstractString="~/.julia/dev"`: パッケージを配置するディレクトリ。
  * `host::AbstractString="github.com"`: パッケージが存在するコードホスティングサービスのURL。
  * `julia::VersionNumber=v"1.6.7"`: 許可される最小Juliaバージョン。

### テンプレートプラグイン

  * `plugins::Vector{<:Plugin}=Plugin[]`: テンプレートで使用される[`Plugin`](@ref)のリスト。デフォルトのプラグインは[`ProjectFile`](@ref)、[`SrcDir`](@ref)、[`Tests`](@ref)、[`Readme`](@ref)、[`License`](@ref)、[`Git`](@ref)、[`CompatHelper`](@ref)、[`TagBot`](@ref)および[`GitHubActions`](@ref)です。デフォルトのプラグインを無効にするには、否定された型を渡します: `!PluginType`。デフォルトのプラグインを無効にするのではなく上書きするには、自分のインスタンスを渡します。

### インタラクティブモード

  * `interactive::Bool=false`: キーワードでテンプレートオプションを指定するだけでなく、一連のプロンプトに従ってテンプレートを構築することもできます。インタラクティブにテンプレートを作成するには、このキーワードを`true`に設定します。類似の[`generate`](@ref)関数も参照してください。

---

`Template`からパッケージを作成するには、次の構文を使用します:

```julia
julia> t = Template();

julia> t("PkgName")
```
