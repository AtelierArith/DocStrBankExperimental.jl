```
create_elem_restriction_curl_oriented(
    ceed::Ceed,
    nelem,
    elemsize,
    ncomp,
    compstride,
    lsize,
    offsets::AbstractArray{CeedInt},
    curlorients::AbstractArray{CeedInt},
    mtype::MemType=MEM_HOST,
    cmode::CopyMode=COPY_VALUES,
)
```

curl指向の`CeedElemRestriction`を作成します。

!!! warning "ゼロベースのインデックス"
    以下の表記では、**ゼロベースのインデックス**を使用しています。libCEEDはオフセットインデックスがゼロベースであることを期待しています。


# 引数:

  * `ceed`:        [`Ceed`](@ref)オブジェクト
  * `nelem`:       `offsets`配列で記述される要素の数
  * `elemsize`:    要素ごとのサイズ（"ノード"の数）
  * `ncomp`:       補間ノードごとのフィールドコンポーネントの数（スカラー場の場合は1）
  * `compstride`:  同じLベクトル"ノード"のコンポーネント間のストライド。ノード$i$、コンポーネント$j$、要素$k$のデータは、Lベクトルのインデックス`offsets[i + k*elemsize] + j*compstride`で見つけることができます。
  * `lsize`:       Lベクトルのサイズ。このベクトルは、この制限によって与えられる要素やフィールドよりも大きい場合があります。
  * `offsets`:     形状`(elemsize, nelem)`の配列。列$i$は、要素$i$に対応する未知数のオフセット（入力[`CeedVector`](@ref)への）を保持する順序付きリストを持ち、$0 \leq i < \textit{nelem}$です。すべてのオフセットは範囲$[0, \textit{lsize} - 1]$内でなければなりません。
  * `curlorients`: 形状`(3 * elemsize, nelem)`の配列で、行優先の三重対角行列を表します（`curlorients[0, i] = curlorients[3 * elemsize - 1, i] = 0`、ここで$0 \leq i < \textit{nelem}$）で、制限時に要素の未知数に適用されます。
  * `mtype`:       `offsets`配列のメモリタイプ、[`MemType`](@ref)を参照
  * `cmode`:       `offsets`配列のコピー方式、[`CopyMode`](@ref)を参照
