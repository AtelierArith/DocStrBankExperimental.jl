```
I = mat2img(mat::Array{<:Unsigned}; x=[], y=[], hdr=[], proj4="", wkt="", cmap=GMTcpt(), kw...)
```

2Dの'mat'配列と`hdr` 1x9 [xmin xmax ymin ymax zmin zmax reg xinc yinc] ヘッダ記述子を取り、GMTimage型を返します。`hdr`の代わりに、XおよびY座標を持つベクトルxとyのペアを提供します。オプションとして、`hdr`引数を省略することができ、その場合は`mat`のみから計算されますが、その場合x=1:ncol, y=1:nrowになります。`mat`が3DのUInt16配列である場合、自動的にUInt8 RGB画像を計算します。その場合、`cmap`は無視されます。しかし、変換を望まない場合は、オプション`noconv=true`を使用します。

```
I = mat2img(mat::Array{UInt16}; x=[], y=[], hdr=[], proj4::String="", wkt::String="", kw...)
```

UInt16の`mat`配列を取り、UInt8にスケールダウンします。入力は2Dまたは3Dで可能です。`kw`変数`stretch`が使用される場合、`stretch`の間隔を[0 255]に引き伸ばします。このオプションを使用して画像のヒストグラムを引き伸ばします。`stretch`がスカラーの場合、`stretch`を超える値を[0 255]にスケールします。

  * stretch = [v1 v2] は、すべての値 >= v1 && <= v2 を[0 255]にスケールします。
  * stretch = [v1 v2 v3 v4 v5 v6] は、最初のバンドを >= v1 && <= v2 を[0 255]にスケールし、2番目を >= v3 && <= v4、3番目も同様にします。
  * stretch = :auto | "auto" | true | 1 は、ヒストグラムの閾値から得られた値から自動的に引き伸ばしを行います。

`kw...`のキーワード引数は、[:layout :mem_layout], [:names] および [:metadata] を検索します。
