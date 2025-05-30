```
planar_cubicalを描画する(cc::LefschetzComplex,
                    coords::Vector{<:Vector{<:Real}},
                    fname::String;
                    [hfac::Real=1.2,]
                    [vfac::Real=1.2,]
                    [cubefac::Real=0,]
                    [pdim::Vector{Bool}=[true,true,true],]
                    [pv::Bool=false])

```

平面立方体複合体の画像を作成します。

ベクトル `coords` には、立方体複合体 `cc` のすべての頂点の座標が含まれています。画像は `fname` という名前のファイルに保存され、拡張子によって画像の種類が決まります。受け入れられるのは `.pdf`、`.svg`、`.png`、および `.eps` です。オプションの定数 `hfac` と `vfac` には、水平および垂直のスケールベクトルが含まれています。オプションの引数 `cubefac` は、プロットのための基本立方体の辺の長さを指定し、そうでない場合は自動的に決定されます。ベクトル `pdim` は、どのセルの次元をプロットするかを指定し、`pdim[k]` は次元 `k-1` を表します。最後に、引数 `pv=true` を渡すと、ファイルを保存するだけでなく、プレビューも表示されます。

# 例

次のコマンドを使用して立方体複合体を作成したとします。

```julia
cubes = ["00.11", "01.01", "02.10", "11.10", "11.01", "22.00"]
coords = [[0,0],[0,1],[0,2],[1,0],[1,1],[1,2],[2,1],[2,2]]
cc = create_cubical_complex(cubes)
fname = "cc_plot_test.pdf"
```

次に、次のコードはラベルなしで単体複合体の画像を作成しますが、プレビューは表示されます。

```julia
plot_planar_cubical(cc, coords, fname, pv=true)
```

複合体のエッジのみをプロットしたいが、頂点や長方形はプロットしたくない場合は、次のように使用できます。

```julia
plot_planar_cubical(cc, coords, fname, pv=true, pdim=[false,true,false])
```
