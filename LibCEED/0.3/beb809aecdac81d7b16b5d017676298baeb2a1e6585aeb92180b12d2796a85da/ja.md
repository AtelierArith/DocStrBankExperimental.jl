```
create_elem_restriction_oriented(
    ceed::Ceed,
    nelem,
    elemsize,
    ncomp,
    compstride,
    lsize,
    offsets::AbstractArray{CeedInt},
    orients::AbstractArray{Bool},
    mtype::MemType=MEM_HOST,
    cmode::CopyMode=COPY_VALUES,
)
```

オリエンテーション付きの `CeedElemRestriction` を作成します。

!!! warning "ゼロベースのインデックス"
    以下の表記では、**ゼロベースのインデックス**を使用しています。libCEEDはオフセットインデックスがゼロベースであることを期待しています。


# 引数:

  * `ceed`:       [`Ceed`](@ref) オブジェクト
  * `nelem`:      `offsets` 配列で記述される要素の数
  * `elemsize`:   要素ごとのサイズ（"ノード"の数）
  * `ncomp`:      補間ノードごとのフィールドコンポーネントの数（スカラー場の場合は1）
  * `compstride`: 同じLベクトルの"ノード"間のコンポーネントのストライド。ノード $i$、コンポーネント $j$、要素 $k$ のデータは、Lベクトルのインデックス `offsets[i               + k*elemsize] + j*compstride` にあります。
  * `lsize`:      Lベクトルのサイズ。このベクトルは、この制限によって与えられる要素やフィールドよりも大きい場合があります。
  * `offsets`:    形状 `(elemsize, nelem)` の配列。列 $i$ は、要素 $i$ に対応する未知数のオフセット（入力 [`CeedVector`](@ref) への）を順序付けたリストを保持します。ここで、$0 \leq i < \textit{nelem}$。すべてのオフセットは、範囲 $[0, \textit{lsize} - 1]$ にある必要があります。
  * `orients`:    形状 `(elemsize, nelem)` の配列で、正のオリエンテーションにはブール値 false、オリエンテーションを反転させるには true を持ちます。
  * `mtype`:      `offsets` 配列のメモリタイプ、[`MemType`](@ref) を参照
  * `cmode`:      `offsets` 配列のコピー方式、[`CopyMode`](@ref) を参照
