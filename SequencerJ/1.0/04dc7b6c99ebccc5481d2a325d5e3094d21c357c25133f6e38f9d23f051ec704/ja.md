```
sequence(A::VecOrMat{T}; 
    scales=nothing,
    metrics=ALL_METRICS,
    grid=nothing,
    ) where {T <: Real}
```

提供された `m x n` 行列（または m 本のベクトルのベクトル n）を分析し、各データ列に対して1次元の統計的指標を1つ以上適用します。これは、データを小さな行セットに分割した後に行われる可能性があります。列は、各指標とスケールの組み合わせごとにペアワイズで比較され、n x n の距離行列が作成され、これは新しいアルゴリズムを使用してグラフとして分析されます。アルゴリズムの詳細は、以下に引用された D. Baron と B. Ménard の論文に記載されています。

```julia
sequence(A, metrics=ALL_METRICS, scales=nothing)
```

または同等のものとして：

```julia
sequence(A)
```

`metrics=ALL_METRICS` と `scales=nothing` はデフォルトです。1つの指標のみを指定したい場合は、それを1タプルでラップする必要があります。例えば、KLダイバージェンスのみを使用するには、次のように書きます：

```julia
sequence(A, metrics=(KLD,), scales=nothing
```

`scales` キーワードを使用して、データを分割する「チャンク」の数をタプルとして指定します。例えば：

```julia
sequence(A, scales=(1,3,5))
```

`autoscale` モード（デフォルトで `scales=nothing` として有効）では、SequencerJ はサンプル列（現在は10%）に対して Sequencer を実行し、最も大きな伸長をもたらすスケールを選択することに基づいて「最適なスケール」を見つけます。

1次元のグリッドを提供することもできます。このグリッド - そのデルタは距離計算に影響します - は非負の実数（Float16、Float32、または Float64）でなければなりません。グリッドの長さは A の行数と等しくなければなりません。

```julia
julia> sequence(A; metrics=(WASS1D,L2), grid=collect(0.5:0.5:size(A,1))) # グリッドは次元1に沿った A のサイズと等しくなければなりません
```

Sequencer アルゴリズムとその応用について説明した論文は [Arxiv](https://arxiv.org/abs/2006.13948) で見つけることができます。
