```
make_current_mnf(path_or_name) -> path
make_current_mnf(; current::Bool) -> path
make_current_mnf(env::EnvInfo) -> path
```

[バージョン管理されたマニフェスト](https://pkgdocs.julialang.org/v1/toml-files/#Different-Manifests-for-Different-Julia-versions)を作成します。

`make_current_mnf(; current=true)`と呼び出すと、現在の環境がこの関数によって処理されます。

`path_or_name`は、`@`で始まる共有環境の名前、または任意の環境へのパスです。

  * 現在実行中のJuliaバージョンがバージョン固有のマニフェストをサポートしていない場合、何もしません。
  * それ以外の場合、現在のJuliaのためのバージョン管理されたマニフェストがすでに存在する場合、何もしません。
  * それ以外の場合、環境が現在のJuliaバージョンのメイン共有環境（例：Julia v1.11の場合の"@v1.11"）である場合、何もしません。
  * それ以外の場合、指定されたディレクトリに古いJuliaのための（バージョン管理された）マニフェストが存在する場合、それを現在のJuliaバージョンに従って名前を付けたファイル（例：`Manifest-v1.11.toml`）にコピーします。
  * それ以外の場合、空のものを作成します。

作成されたまたは既存のマニフェストへのパスを返します。

この関数は公開されており、エクスポートされていません。
