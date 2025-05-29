```
BotConfig(package_name::AbstractString ; exclusions, os, else_os, version, else_version, package_path, precompiles_rootpath, subst, tmin)
```

SnoopCompileボットの構成を作成します。`package_name`はパッケージの名前です。このオブジェクトは[`snoop_bot`](@ref)および[`snoop_bench`](@ref)に渡されます。

次のオプションの**キーワード**引数を指定できます：

  * `exclusions` : プリコンパイルから除外する関数の文字列（またはRegExp）のベクター
  * `os`: プリコンパイルステートメントをサポートする文字列（またはRegExp）のベクター。

例: `os = ["windows", "linux"]`

  * `else_os`: 特定のオペレーティングシステムのプリコンパイルファイルをデフォルトとして使用したい場合は、`else_os`をそのosの名前に設定します。この引数を渡さないと、`os`に明示的にリストされている以外のオペレーティングシステムでのプリコンパイルはスキップされます。

例: `else_os = "linux"`

  * `version`: プリコンパイルシグネチャを生成するために使用されるJuliaのバージョンのベクター。

例: `version = [v"1.1", v"1.4.2", "nightly"]`

生成されたプリコンパイルシグネチャは、Juliaのパッチバージョンに対して有効であると仮定されます（例: v"1.4.2"を与えるとv"1.4.0"からv"1.4.9"をサポートします）。

  * `else_version`: 他の`version`のデフォルトシグネチャを生成するために使用されるJuliaのバージョン。

この引数を渡さないと、`version`に明示的にリストされている以外のJuliaバージョンでのプリコンパイルはスキップされます。

例: `else_version = v"1.4.2"`

  * `yml_path`: `os`と`version`をBotConfigに直接渡す代わりに、GitHubアクションのYAMLパスまたはファイル名である`yml_path`を渡すことができます。

ジョブ名は`SnoopCompile`であると仮定します。

例: `yaml_path = "SnoopCompile.yml"`

  * `package_path`: パッケージのメイン`.jl`ファイルへのパス（`pathof`に似ています）。デフォルトのパスは`pathof_noload(package_name)`です。
  * `precompiles_rootpath`: プリコンパイルファイルが保存されるパス。デフォルトのパスは" :(dirname(dirname(package_path)))/deps/SnoopCompile/precompile"です。
  * `subst` : 他のパッケージのプリコンパイルステートメントと置き換えるための文字列（またはRegExp）のペアのベクター、例えば`["ImageTest" => "Images"]`。
  * `tmin`: `tmin`よりも短い時間で推論されるメソッドはプリコンパイルステートメントに追加されません。デフォルトは0です。
  * `check_eval`: デフォルトでは、ボットは`eval`できないプリコンパイルステートメントを破棄します。

稀なケース（スヌーピングが非常に時間がかかる場合）では、印刷されたエラーを使用して問題のある関数を`exclusions`に追加し、将来の実行のために`check_eval=false`を設定することで手動で行いたい場合があります。

# 例

```julia
botconfig1 = BotConfig(
  "Zygote";                            # パッケージ名（この構成が存在するもの）
  os = ["linux", "windows", "macos"],  # プリコンパイルするオペレーティングシステム
  version = [v"1.4.2", v"1.3.1"],      # サポートされるJuliaバージョン
  exclusions = ["SqEuclidean"],         # プリコンパイル時に問題が発生する関数（名前で）を除外
)

botconfig2 = BotConfig(
  "Zygote";                            # パッケージ名（この構成が存在するもの）
  yml_path = "SnoopCompile.yml"        # `SnoopCompile.yml`から`os`と`version`を解析
  exclusions = ["SqEuclidean"],         # プリコンパイル時に問題が発生する関数（名前で）を除外
)

# 完全な例：
BotConfig("MatLang", exclusions = ["badfunction"], os = ["linux", "windows", "macos"], else_os = "linux", version = ["1.4.2", "1.2", "1.0.5"], else_version = "1.4.2" )

# 他の可能性のための異なる例：
BotConfig("MatLang")

BotConfig("MatLang", exclusions = ["badfunction"])

BotConfig("MatLang", os = ["linux", "windows"])

BotConfig("MatLang", os = ["windows", "linux"], else_os = "linux")

BotConfig("MatLang", version = [v"1.1", v"1.4.2"])

BotConfig("MatLang", version = [v"1.1", v"1.4.2"], else_version = v"1.4.2")

BotConfig("MatLang", os = ["linux", "windows"], version = [v"1.1", v"1.4.2"])
```
