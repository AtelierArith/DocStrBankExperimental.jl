```
NCvar
```

NetCDFファイルに変数を書き込むために必要な情報を含むデータ構造。

データをメモリにロードする代わりに、入力ファイル名のリストを提供することができます（`Bindata`を参照）。

属性（`atts`）: 1. 文字列属性はnetcdfファイルに書き込まれます; 2. "readdata"NCTiles.readataという関数属性が、`NCTiles.readata`のデフォルトの代わりに使用されます。

```
struct NCvar
    name::String
    units::String
    dims
    values
    atts::Union{Dict,Nothing}
    backend::Module
end
```
