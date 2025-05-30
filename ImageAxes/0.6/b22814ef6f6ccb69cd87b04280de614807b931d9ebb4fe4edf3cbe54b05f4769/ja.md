```
A = StreamingContainer{T}(f!, parent, streamingaxes::Axis...)
```

スライスを変更することが高コストまたは制限される可能性のある1つ以上の軸を持つ配列のようなオブジェクト。典型的な例はAVIストリームで、同じフレーム内のピクセルにアクセスするのは速いが、フレーム間をジャンプするのは遅いかもしれません。

画像の各スライスの平均で割ってから値を返す簡単な例を示します。

```
A = AxisArrays.AxisArray(reshape(1:36, 3, 3, 4))

function f!(buffer, slice)
    meanslice = mean(slice)
    buffer .= slice./meanslice
end

B = StreamingContainer{Float64}(f!, A, AxisArrays.axes(A)[3])

julia> A[:,:,1]
3×3 AxisArray{Int64,2,Array{Int64,2},Tuple{Axis{:row,Base.OneTo{Int64}},Axis{:col,Base.OneTo{Int64}}}}:
 1  4  7
 2  5  8
 3  6  9

julia> B[:,:,1]
3×3 Array{Float64,2}:
 0.2  0.8  1.4
 0.4  1.0  1.6
 0.6  1.2  1.8
```

ユーザー提供の `f!` 関数は次の引数を取る必要があります：

```
f!(buffer, slice)
```

ここで `buffer` はシリーズのスライスを保持できる空の配列であり、`slice` は現在の入力スライスを保持します。

`StreamingContainer` は `AbstractArray` のサブタイプではないことに注意が必要ですが、配列インターフェースの多く（`eltype`、`ndims`、`axes`、`size`、`getindex`、および `IndexStyle`）はサポートされています。StreamingContainer `A` は AxisArray から構築できますが、同じ関数をサポートする限り、他の「親」オブジェクト（配列でないものも含む）から構築することもできます。いずれの場合も、親は標準の AxisArray 関数 `axes`、`axisnames`、`axisvalues`、および `axisdim` をサポートする必要があります。このサポートは `StreamingContainer` にも拡張されます。

さらに、StreamingContainer `A` は次のことをサポートします。

```
getindex!(dest, A, axt::Axis{:time}, ...)
```

ストリーミングされた軸に沿ったスライスを取得するために（ここでは `:time` が `A` のストリーミングされた軸であると仮定されています）。これを直接実装することもできます（`A` のパラメータに基づいてディスパッチする）、または（親が `AbstractArray` の場合）フォールバックに依存することもできます。

```
A.getindex!(dest, view(parent, axs...))
```

ここで `A.getindex! = f!` は構築時に引数として渡されます。`dest` は次元数 `ndims(parent)-length(streamingaxes)` を持つ必要があります。

オプションで、[`StreamIndexStyle(typeof(parent),typeof(f!))`](@ref) を定義します。
