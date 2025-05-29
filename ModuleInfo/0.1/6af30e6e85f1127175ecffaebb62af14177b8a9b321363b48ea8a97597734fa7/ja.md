```
PackageIndex(modules; kwargs...)
```

`modules`を定義するパッケージのインデックスを作成します。作成されたインデックスには、パッケージに関連する以下のデータの表が含まれます：

  * パッケージ
  * モジュール
  * シンボル
  * メソッド
  * ドキュメント文字列
  * ソースファイル
  * バインディング

## キーワード引数

  * `cache = false`: インデックスを保存するために使用するキャッシュ。`true`の場合、デフォルトのグローバルファイルベースのキャッシュ（`ModuleInfo.CACHE[]`）を使用します。また、[`InfoCache`](#)を直接渡すこともできます。キャッシュが使用される場合、すでにインデックスされたパッケージは再インデックスされません。開発中のパッケージは、キャッシュが作成されて以来変更があった場合に再インデックスされます。
  * `verbose = false`: `true`の場合、実行中にどのパッケージがインデックスされているかを表示します。
  * `packages = nothing`: インデックスされるパッケージを指定されたものに制限するために`Vector{String}`を渡します。`recurse`オプションを使用しているときに、いくつかの依存関係のみをインデックスしたい場合に便利です。
  * `recurse = 0`: `packages`の依存関係にどれだけのレベルで再帰するか。デフォルトの`0`は依存関係がインデックスされないことを意味します。`1`は、`packages`内の各パッケージの直接の依存関係のみがインデックスされることを意味します。
  * `pkgtags = Dict{String, String}()`: パッケージが保存されるバージョンを上書きするために使用できる`package_name => version_name`のマッピング。

## 例

パッケージをインデックスする：

{cell}

```julia
using ModuleInfo
pkgindex = PackageIndex([ModuleInfo])
```

パッケージとその直接の依存関係をインデックスする：

{cell}

```julia
using ModuleInfo
pkgindex = PackageIndex([ModuleInfo], recurse = 1)
ModuleInfo.getid.(pkgindex.packages)
```
