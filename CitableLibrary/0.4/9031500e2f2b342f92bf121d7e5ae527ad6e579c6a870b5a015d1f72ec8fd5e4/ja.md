`CiteLibrary`を構築します。

```julia
library(collections; libname, liburn, license, cexversion)

```

## オプションのパラメータ

  * `liburn` このライブラリの一意の識別子。`Urn`のサブタイプでなければなりません。
  * `libname` ライブラリの名前（`label`によって返される値）
  * `license` ライセンス。デフォルトはcc-nc-byです。
  * `cexversion` ライブラリのシリアル化に使用されるCEX標準のバージョン。デフォルトは現在のバージョンです。
