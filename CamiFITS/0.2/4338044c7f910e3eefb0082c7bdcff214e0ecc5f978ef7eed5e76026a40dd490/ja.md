```
fits_extend(f::FITS, data [; hdutype="IMAGE"])
fits_extend(filnam::String, data [; hdutype="IMAGE"])
```

[`FITS`](@ref) オブジェクト `f` は、`hdutype` キーワードの形式の `data` から構築された [`FITS_HDU`](@ref) オブジェクトによって拡張されます。

ショートハンド関数: ディスク上のファイル名 `filnam` の場合

```
julia> f = fits_extend(filnam, data; hdutype="foo")
```

は次のように等価です

```
julia> f = fits_read(filnam);

julia> fits_extend(f, data; hdutype="foo")
```

注: 保存手順の詳細については（フローダイアグラムには表示されていません）

  * [`fits_save`](@ref) を参照してください。

![Image](../assets/fits_extend.png)

#### 例:

```
julia> filnam = "foo.fits";

julia> fits_create(filnam; protect=false);

julia> table = let
        [true, 0x6c, 1081, 0x0439, 1.23, 1.01f-6, 1.01e-6, 'a', "a", "abc"],
        [false, 0x6d, 1011, 0x03f3, 23.2, 3.01f-6, 3.01e-6, 'b', "b", "abcdef"]
        end;

julia> fits_extend(filnam, table; hdutype="table");

julia> fits_info(filnam, 2; hdr=false)
2-element Vector{String}:
 " 1 108 1081 1081  1.23 1.01E-6 1.01D-6 a a    abc"
 " 0 109 1011 1011 23.20 3.01E-6 3.01D-6 b b abcdef"

julia> rm(filnam)
```
