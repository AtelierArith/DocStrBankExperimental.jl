```
create_elem_restriction_strided(ceed::Ceed, nelem, elemsize, ncomp, lsize, strides)
```

ストライド付き `CeedElemRestriction` を作成します。

!!! warning "ゼロベースのインデックス"
    以下の表記では、**ゼロベースのインデックス**を使用しています。libCEEDはオフセットインデックスが0ベースであることを期待しています。


# 引数:

  * `ceed`:     [`Ceed`](@ref) オブジェクト
  * `nelem`:    制限によって記述される要素の数
  * `elemsize`: 要素ごとのサイズ（"ノード"の数）
  * `ncomp`:    補間ノードごとのフィールドコンポーネントの数（スカラー場の場合は1）
  * `lsize`:    Lベクトルのサイズ。このベクトルは、この制限によって与えられる要素やフィールドよりも大きい場合があります。
  * `strides`:  [ノード、コンポーネント、要素] の間のストライド用の配列。ノード $i$、コンポーネント $j$、要素 $k$ のデータは、Lベクトルのインデックス `i*strides[0] + j*strides[1] + k*strides[2]` にあります。[`STRIDES_BACKEND`](@ref) は、Ceed バックエンドによって作成されたベクトルと共に使用できます。
