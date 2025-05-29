```
readrplraw(rplfilename::AbstractString, rawfilename::AbstractString)
readrplraw(rplio::IO, rawio::IO)
```

IOまたはファイル名からRPL/RAWファイルペアをArrayオブジェクトに読み込みます。リーダーは:bigendian、:littleendianの順序と、:vectorまたは:imageの整列をサポートしています。Arrayは非常に大きくなる可能性があるため、データが不要になったら変数に`nothing`を割り当てる（またはスコープから外れるのを許可する）ことで関連するメモリを解放し、`GC.gc()`を呼び出してガーベジコレクションを強制することが有益です。

```
* 順序: 個々のデータ項目は`:littleendian`または`:bigendian`のいずれかです。
** `:littleendian` => Intel/AMDなど
** `:bigendian` => ARM/PowerPC/Motorola
* 整列: ファイル内のデータは`:vector`または`:image`として整理できます。ただし、データは
```

Arrayとして返されるときに「ベクトル」形式に再編成されます。     **`:vector` => スペクトル/データベクトルがピクセルごとの連続ブロックとして     ** `:image` => 各データチャネルが画像プレーンに整理されます     * データ型: 符号付き/符号なしの8/16/32ビット整数または16ビット/32ビット/64ビット浮動小数点数

```
readrplraw(filenamebase::AbstractString)::Array{<:Real}
```

ファイル名base*".rpl"およびファイル名base*".raw"をArrayに読み込みます。RAWファイル内の値のデータ型を維持します。

#### .rplファイルの標準LISPIXパラメータ

.rplファイルは9行で構成されています。各行は「key<tab>value」で構成されており、パラメータ名とパラメータ値の間には1つのタブと、場合によっては他のスペースがあります。パラメータ名は大文字と小文字を区別しません。ファイルの最初の行は「key<tab>value」です。以降の行には、この表に記載されているキーと値が含まれています。

| **key**     | **value** | **description**                 |
|:----------- | ---------:|:------------------------------- |
| width       |       849 | ピクセル/行       整数                 |
| height      |       846 | 行                 整数            |
| depth       |      4096 | 画像またはスペクトルポイント   整数             |
| offset      |         0 | スキップするバイト        整数             |
| data-length |         1 | ピクセルあたりのバイト      1, 2, 4, または 8 |
| data-type   |  unsigned | 符号付き、符号なし、または浮動小数点              |
| byte-order  | dont-care | ビッグエンディアン、リトルエンディアン、または気にしない    |
| record-by   |    vector | 画像、ベクトル、または気にしない                |

この.rplファイルは、画像が849ピクセルの幅と846ピクセルの高さを持ち、深さ次元に4096レベルがあることを示しています。
