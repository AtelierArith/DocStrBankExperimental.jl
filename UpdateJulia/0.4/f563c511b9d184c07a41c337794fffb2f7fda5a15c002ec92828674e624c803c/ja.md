```
update_julia(version::AbstractString="")
```

最新のJuliaをhttps://julialang.orgからインストールします。

`version`が指定されている場合、`version`で始まる最新のバージョンをインストールします。`version == "nightly"`の場合、最先端のナイトリーバージョンをインストールします。

# キーワード引数

動作フラグ

  * `dry_run = false` 実際のダウンロードとインストールをスキップします
  * `verbose = dry_run` すべての引数の最終値を出力します
  * `migrate_packages = <既存のグローバル環境なしでJuliaの後のバージョンにアップグレード>` デフォルトのグローバル環境でパッケージを移行するかどうか。`true`、`false`、または`:force`のいずれかです。`:force`のみが既存のProject.tomlを置き換えます

宛先

  * `aliases = ["julia", "julia-$(v.major).$(v.minor)", "julia-$v"]` インストールされたJuliaのバージョンに対して作成を試みるエイリアス。いずれにせよ、安定版を不安定版で置き換えたり、同じ安定性の古いバージョンで新しいバージョンを置き換えたりすることはありません。
  * `systemwide = false` すべてのユーザーにインストールします。`false`は現在のユーザーのみにインストールします。
  * `install_location = systemwide ? "/opt" : "/home/terasaki/.julia/juliaup"` インストールされたバイナリを置くディレクトリ
  * `bin = systemwide ? "/usr/local/bin" : "/home/terasaki/.local/bin"` バイナリへのリンクを保存するディレクトリ

ソース

  * `os_str = "linux"` オペレーティングシステムの文字列表現："linux"、"mac"、"winnt"、または"freebsd"。
  * `arch = "x86_64"` CPUアーキテクチャの文字列表現："x86_64"、"i686"、"aarch64"、"armv7l"、または"powerpc64le"。
  * `v = ...` インストールする`VersionNumber`
  * `url = ...` 明示的に`url`を設定した場合、そのバージョンをダウンロードするためのURL。`url`を明示的に設定した場合、`v`も明示的に設定しないと異なる場合があります。
