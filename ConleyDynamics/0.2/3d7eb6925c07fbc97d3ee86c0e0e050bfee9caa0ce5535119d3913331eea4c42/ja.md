```
create_planar_mvf(lc::LefschetzComplex, coords::Vector{Vector{Float64}}, vf)
```

正規ベクトル場から平面多ベクトル場を作成します。

この関数は、平面のLefschetz複体 `lc` と、複体内のすべての0次元セルの座標のベクトル `coords` を期待します。さらに、基になるベクトル場は、関数 `vf(z::Vector{Float64})::Vector{Float64}` によって指定され、入力および出力のベクトルは長さ2です。関数 `create_planar_mvf` は、`lc` 上の多ベクトル場 `mvf` を返し、その後、例えば関数 `connection_matrix` を使用してさらに分析できます。

入力データ `lc` と `coords` は、次のいずれかの方法を使用して生成できます：

  * `create_cubical_rectangle`
  * `create_simplicial_rectangle`
  * `create_simplicial_delaunay`

各場合において、提供された座標ベクトルは、変換関数 `convert_planar_coordinates` を使用して正しいバウンディングボックスの値に変換できます。

# 例 1

サンプルベクトル場を次のコマンドを使用して定義するとします。

```julia
function samplevf(x::Vector{Float64})
    #
    # 非自明なモース分解を持つサンプルベクトル場
    #
    x1, x2 = x
    y1 = x1 * (1.0 - x1*x1 - 3.0*x2*x2)
    y2 = x2 * (1.0 - 3.0*x1*x1 - x2*x2)
    return [y1, y2]
end
```

まず、次のコマンドを使用して、囲むボックスの三角分割を作成します。この場合、ボックスは `[-2,2] x [-2,2]` で与えられます。

```julia
n = 21
lc, coords = create_simplicial_rectangle(n,n);
coordsN = convert_planar_coordinates(coords,[-2.0,-2.0],[2.0,2.0]);
```

次に、多ベクトル場は次のように生成されます。

```julia
mvf = create_planar_mvf(lc,coordsN,samplevf);
```

そして、次のコマンドを使用して

```julia
cm = connection_matrix(lc, mvf);
cm.conley
full_from_sparse(cm.matrix)
```

最終的に、このベクトル場が9つのモース集合と12の接続軌道を持つモース分解を生じることを示します。次のコマンドを使用して

```julia
fname = "morse_test.pdf"
plot_planar_simplicial_morse(lc, coordsN, fname, cm.morse, pv=true)
```

これらのモース集合を視覚化できます。画像は `fname` に保存されます。

# 例 2

周期的な軌道を持つ例は、次のベクトル場を使用して生成できます。

```julia
function samplevf2(x::Vector{Float64})
    #
    # 非自明なモース分解を持つサンプルベクトル場
    #
    x1, x2 = x
    c0 = x1*x1 + x2*x2
    c1 = (c0 - 4.0) * (c0 - 1.0)
    y1 = -x2 + x1 * c1
    y2 =  x1 + x2 * c1
    return [-y1, -y2]
end
```

モース分解は次のように計算できます。

```julia
n2 = 51
lc2, coords2 = create_cubical_rectangle(n2,n2);
coords2N = convert_planar_coordinates(coords2,[-4.0,-4.0],[4.0,4.0]);
mvf2 = create_planar_mvf(lc2,coords2N,samplevf2);
cm2 = connection_matrix(lc2, mvf2);
cm2.conley
cm2.poset
full_from_sparse(cm2.matrix)

fname2 = "morse_test2.pdf"
plot_planar_cubical_morse(lc2, fname2, cm2.morse, pv=true)
```

この場合、3つのモース集合が得られます：1つは安定平衡、1つは不安定周期軌道、最後の1つは安定周期軌道です。
