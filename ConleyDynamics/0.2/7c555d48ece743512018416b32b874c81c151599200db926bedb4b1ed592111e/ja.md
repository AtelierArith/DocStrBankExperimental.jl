```
planar_simplicialを描画する(sc::LefschetzComplex,
                       coords::Vector{<:Vector{<:Real}},
                       fname::String;
                       [mvf::CellSubsets=Vector{Vector{Int}}([]),]
                       [labeldir::Vector{<:Real}=Vector{Int}([]),]
                       [labeldis::Real=8,]
                       [hfac::Real=1.2,]
                       [vfac::Real=1.2,]
                       [sfac::Real=0,]
                       [pdim::Vector{Bool}=[true,true,true],]
                       [pv::Bool=false])

```

平面単純複体の画像を作成し、指定されている場合はその上にフォーマンベクトル場を描画します。

ベクトル`coords`は、単純複体`sc`のすべての頂点の座標を含みます。画像は`fname`という名前のファイルに保存され、拡張子によって画像のタイプが決まります。受け入れられるのは`.pdf`、`.svg`、`.png`、および`.eps`です。

オプションの`mvf`が指定され、フォーマンベクトル場である場合、このフォーマンベクトル場も描画されます。オプションのベクトル`labeldir`は頂点ラベルの方向を含み、`labeldis`は頂点からの距離を示します。方向は0から4の実数でなければならず、0,1,2,3はそれぞれE,N,W,Sに対応します。オプションの定数`hfac`と`vfac`は水平および垂直スケールベクトルを含み、`sfac`は均一スケールを示します。`sfac=0`の場合、後者は自動的に決定されます。ベクトル`pdim`はセルが描画される次元を指定します。デフォルトでは頂点、エッジ、および三角形が表示されます。最後に、引数`pv=true`を渡すと、ファイルを保存するだけでなくプレビューも表示されます。

# 例

単純複体を次のコマンドを使用して作成したとします。

```julia
sc, coords = create_simplicial_delaunay(300, 300, 30, 20)
fname = "sc_plot_test.pdf"
```

次に、以下のコードはラベルなしで単純複体の画像を作成しますが、プレビューは表示されます。

```julia
plot_planar_simplicial(sc, coords, fname, pv=true)
```

ラベルを表示したい場合は、次のようにします。

```julia
ldir = fill(0.5, sc.ncells);
plot_planar_simplicial(sc, coords, fname, labeldir=ldir, labeldis=10, pv=true)
```

このコマンドは、すべてのラベルを北東方向に10の距離で配置します。
