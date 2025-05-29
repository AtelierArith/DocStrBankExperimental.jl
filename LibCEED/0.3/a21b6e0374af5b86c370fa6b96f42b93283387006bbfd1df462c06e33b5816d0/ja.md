```
create_elem_restriction(
    ceed::Ceed,
    nelem,
    elemsize,
    ncomp,
    compstride,
    lsize,
    offsets::AbstractArray{CeedInt},
    mtype::MemType=MEM_HOST,
    cmode::CopyMode=COPY_VALUES,
)
```

`CeedElemRestriction`を作成します。

!!! warning "ゼロベースのインデックス"
    以下の表記では、**ゼロベースのインデックス**を使用しています。libCEEDはオフセットインデックスがゼロベースであることを期待しています。


# 引数:

  * `ceed`:       [`Ceed`](@ref)オブジェクト
  * `nelem`:      `offsets`配列で説明される要素の数
  * `elemsize`:   要素ごとのサイズ（"ノード"の数）
  * `ncomp`:      補間ノードごとのフィールドコンポーネントの数（スカラー場の場合は1）
  * `compstride`: 同じLベクトル"ノード"のコンポーネント間のストライド。ノード $i$、コンポーネント $j$、要素 $k$ のデータは、Lベクトルのインデックス `offsets[i               + k*elemsize] + j*compstride` にあります。
  * `lsize`:      Lベクトルのサイズ。このベクトルは、この制限によって与えられる要素やフィールドよりも大きい場合があります。
  * `offsets`:    形状 `(elemsize, nelem)` の配列。列 $i$ は、要素 $i$ に対応する未知数のための入力 [`CeedVector`](@ref) へのオフセットの順序付きリストを保持します。ここで、$0 \leq i < \textit{nelem}$。すべてのオフセットは、範囲 $[0, \textit{lsize} - 1]$ にある必要があります。
  * `mtype`:      `offsets`配列のメモリタイプ、[`MemType`](@ref)を参照
  * `cmode`:      `offsets`配列のコピー方式、[`CopyMode`](@ref)を参照
