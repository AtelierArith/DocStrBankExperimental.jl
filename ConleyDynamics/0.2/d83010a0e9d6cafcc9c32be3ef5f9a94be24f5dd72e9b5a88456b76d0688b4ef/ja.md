```
create_spatial_mvf(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf)
```

空間多重ベクトル場を通常のベクトル場から作成します。

この関数は、三次元のLefschetz複体 `lc` と、複体内のすべての0次元セルの座標のベクトル `coords` を期待します。さらに、基になるベクトル場は、関数 `vf(z::Vector{Float64})::Vector{Float64}` によって指定され、入力および出力のベクトルは長さ3です。関数 `create_spatial_mvf` は、`lc` 上の多重ベクトル場 `mvf` を返し、その後、例えば関数 `connection_matrix` を使用してさらに分析できます。

入力データ `lc` と `coords` は、次の2つのタイプのいずれかである必要があります：

  * `lc` は三次元の領域の四面体メッシュです。言い換えれば、基になるLefschetz複体は実際には単体複体であり、ベクトル `coords` には頂点の座標が含まれています。
  * `lc` は三次元の立方体複体です。つまり、空間内の三次元立方体のコレクションの閉包です。頂点の座標は、立方体格子内の元の位置からわずかに摂動されることがありますが、複体の全体的な構造が保持されている限りです。その場合、面は直線のエッジを持つベジエ曲面として解釈されます。

# 例 1

サンプルベクトル場を次のコマンドを使用して定義するとします。

```julia
function samplevf(x::Vector{Float64})
    #
    # 非自明なモース分解を持つサンプルベクトル場
    #
    x1, x2, x3 = x
    y1 = x1 * (1.0 - x1*x1)
    y2 = -x2
    y3 = -x3
    return [y1, y2, y3]
end
```

まず、次のコマンドを使用して、興味深い動力学をカバーする立方体複体を作成します。例えば、捕獲領域 `[-1.5,1.5] x [-1,1] x [-1,1]` を使用します。

```julia
lc, coords = create_cubical_box(3,3,3);
coordsN = convert_spatial_coordinates(coords,[-1.5,-1.0,-1.0],[1.5,1.0,1.0]);
```

次に、次のようにして多重ベクトル場を生成します。

```julia
mvf = create_spatial_mvf(lc,coordsN,samplevf);
```

そして、次のコマンドを使用します。

```julia
cm = connection_matrix(lc, mvf);
cm.conley
full_from_sparse(cm.matrix)
```

最終的に、このベクトル場が3つのモース集合と2つの接続軌道を持つモース分解を生じることを示します。 ```
