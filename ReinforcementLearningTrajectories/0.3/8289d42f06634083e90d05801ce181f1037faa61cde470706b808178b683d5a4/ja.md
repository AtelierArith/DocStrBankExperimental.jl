```
NormalizedTraces(traces::AbstractTraces, normalizers::NamedTuple)
NormalizedTraces(traces::AbstractTraces; trace_normalizer_pairs...)
```

[`AbstractTraces`](@ref) と `Symbol` => [`Normalizer`](@ref) ペアの `NamedTuple` をラップします。トレースに新しい要素を追加する際、`NormalizedTraces` はまず `normalizers` のキーに存在するトレースのモーメントの推定値を更新します。正規化されたトレースをサンプリングする際は、まずサンプルをゼロ平均および単位分散に正規化します。正規化器を持たないトレースは通常通りサンプリングされます。

[`Episodes`](@ref) と組み合わせて使用する場合、`NormalizedTraces` は `Episode` に含まれる内部の `AbstractTraces` ではなく、`Episodes` 構造体をラップする必要があります。そうしないと、各エピソードの後に推定値がリセットされてしまいます。

MultiplexTraces と一緒に使用する場合、あるシンボル（例：:state）に使用される正規化器は、他のシンボル（例：:next_state）にも同じものが使用されます。

スカラー用（[`scalar_normalizer`](@ref) を参照）および配列用（[`array_normalizer`](@ref) を参照）の事前設定された正規化器が提供されています。

# 例

```
t = CircularArraySARTSTraces(capacity = 10, state = Float64 => (5,))
nt = NormalizedTraces(t, reward = scalar_normalizer(), state = array_normalizer((5,)))
# :next_state も正規化されます。 
traj = Trajectory(
    container = nt,
    sampler = BatchSampler(10)
)
```
