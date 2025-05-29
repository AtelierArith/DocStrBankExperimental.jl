```
plot_planar_simplicial_morse(sc::LefschetzComplex,
                             coords::Vector{<:Vector{<:Real}},
                             fname::String,
                             morsesets::CellSubsets;
                             [hfac::Real=1.2,]
                             [vfac::Real=1.2,]
                             [sfac::Real=0,]
                             [pdim::Vector{Bool}=[false,true,true],]
                             [pv::Bool=false])
```

平面単純複体の画像を作成し、モース集合や選択された多重ベクトルも表示します。

ベクトル `coords` には、単純複体 `sc` の各頂点の座標が含まれています。画像は `fname` という名前のファイルに保存され、拡張子によって画像のタイプが決まります。受け入れられるのは `.pdf`、`.svg`、`.png`、および `.eps` です。

ベクトル `morsesets` にはモース集合のリスト、またはより一般的には単純複体の部分集合が含まれています。各 `k` に対して、`morsesets[k]` で説明される集合は異なる色で表示されます。

オプションの定数 `hfac` と `vfac` には、マージンのための水平および垂直スケールベクトルが含まれ、`sfac` は均一スケールを説明します。`sfac=0` の場合、後者は自動的に決定されます。ベクトル `pdim` はセルが描画される次元を指定します。デフォルトではエッジと三角形のみが表示されます。最後に、引数 `pv=true` を渡すと、ファイルを保存するだけでなく、プレビューも表示されます。
