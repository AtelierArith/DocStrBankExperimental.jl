```
rr2([T=Float64], size::NTuple{N, Int};
    offset=CtrFT,
    dims=ntuple(+, N),
    scale=ScaUnit,
    weight=1,
    accumulator=sum)
```

参照ピクセルへの二乗半径を計算します。この場合、`CtrFT`はFFT規約によって定義された中心です。`ScaUnit`は値をスケーリングせずにそのままにします。`offset`と`scale`はそれぞれ`<:Ctr`、`<:Sca`のいずれか、または単に`size`と同じ形状のタプルであることができます。すべてのオプションについては`?Ctr`と`?Sca`を参照してください。`dims`は、操作が実際に行われる次元を指定するためのキーワード引数です。

引数`offset`と`scale`はリストモードをサポートしており、タプルのタプルやタプルのベクトル、または行列を提供すると、関数は自動的に複数のバージョンの重ね合わせを生成します。重ね合わせのタイプは`accumulator`引数によって制御されます。個々の重ね合わせの相対的な強さは`weight`引数を介して制御され、これはタプルまたはベクトルであることができます。以下のVoronoiの例を見てください。

この関数は`IndexFunArray`に基づいているため、配列を表すために必要な完全なメモリを割り当てることはありません。

# 例

```jldoctest
julia> rr2((4, 4))
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 8.0  5.0  4.0  5.0
 5.0  2.0  1.0  2.0
 4.0  1.0  0.0  1.0
 5.0  2.0  1.0  2.0
```

## 参照位置の変更

```jldoctest
julia> rr2((3,3), offset=CtrCorner)
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 0.0  1.0  4.0
 1.0  2.0  5.0
 4.0  5.0  8.0

julia> rr2((4,4), offset=CtrFT)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 8.0  5.0  4.0  5.0
 5.0  2.0  1.0  2.0
 4.0  1.0  0.0  1.0
 5.0  2.0  1.0  2.0

julia> rr2((4,4), offset=CtrMid)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 4.5  2.5  2.5  4.5
 2.5  0.5  0.5  2.5
 2.5  0.5  0.5  2.5
 4.5  2.5  2.5  4.5

julia> rr2((4,4), offset=CtrEnd)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 18.0  13.0  10.0  9.0
 13.0   8.0   5.0  4.0
 10.0   5.0   2.0  1.0
  9.0   4.0   1.0  0.0

julia> rr2((3, 3), offset=(1, 1))
3×3 IndexFunArray{Float64, 2, IndexFunArrays.var"#4#5"{Float64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
 0.0  1.0  4.0
 1.0  2.0  5.0
 4.0  5.0  8.0
```

## スケーリングの変更

```jldoctest
julia> rr((4,4), scale=ScaUnit)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Int64, Int64}}}:
 2.82843  2.23607  2.0  2.23607
 2.23607  1.41421  1.0  1.41421
 2.0      1.0      0.0  1.0
 2.23607  1.41421  1.0  1.41421

julia> rr((4,4), scale=ScaNorm)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.942809  0.745356  0.666667  0.745356
 0.745356  0.471405  0.333333  0.471405
 0.666667  0.333333  0.0       0.333333
 0.745356  0.471405  0.333333  0.471405

julia> rr((4,4), scale=ScaFT)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 0.707107  0.559017  0.5   0.559017
 0.559017  0.353553  0.25  0.353553
 0.5       0.25      0.0   0.25
 0.559017  0.353553  0.25  0.353553

julia> rr((4,4), scale=ScaFTEdge)
4×4 IndexFunArray{Float64, 2, IndexFunArrays.var"#9#10"{Float64, Tuple{Float64, Float64}, Tuple{Float64, Float64}}}:
 1.41421  1.11803   1.0  1.11803
 1.11803  0.707107  0.5  0.707107
 1.0      0.5       0.0  0.5
 1.11803  0.707107  0.5  0.707107

julia> rr2(Int, (3, 3), offset=(1, 1), scale=(10, 10))
3×3 IndexFunArray{Int64, 2, IndexFunArrays.var"#4#5"{Int64, Tuple{Int64, Int64}, Tuple{Int64, Int64}}}:
   0  100  400
 100  200  500
 400  500  800
```

## 選択した次元への適用

以下のコードは、1サイズのトレーリング次元を持つ3D配列を生成します。これはブロードキャスティングに使用できます。

```jldoctest
julia> x = ones(5,6,5);

julia> y=rr2(selectsizes(x,(1,2)))
5×6×1 IndexFunArray{Float64, 3, IndexFunArrays.var"#4#5"{Float64, Tuple{Float64, Float64, Float64}, Tuple{Int64, Int64, Int64}}}:
[:, :, 1] =
 13.0  8.0  5.0  4.0  5.0  8.0
 10.0  5.0  2.0  1.0  2.0  5.0
  9.0  4.0  1.0  0.0  1.0  4.0
 10.0  5.0  2.0  1.0  2.0  5.0
 13.0  8.0  5.0  4.0  5.0  8.0
```

同様に、次元2と3を使用すると、`size(y) == (1,6,5)`の配列が得られます。`Base.size`関数に必要な修正は、現在このパッケージによって提供されています。

## リストモード引数の使用

以下のコードは、ランダムな位置に160のVoronoiセルを生成します。`accumulator`は最小値に設定されており、各ピクセルには最も近いVoronoi中心への二乗距離が得られます。リストモード引数の使用の別の例については`gaussian`を参照してください。

```jldoctest
julia> y = rr2((1000,1000),offset = (1000.0,1000.0) .* rand(2,160), accumulator=minimum);

```

---

```
rr2(arr::AbstractArray; offset=CtrFt, scaling=ScaUnit)
```

これは`rr2(eltype(arr), size(arr), scaling=scaling, offset=offset)`のラッパーです。
