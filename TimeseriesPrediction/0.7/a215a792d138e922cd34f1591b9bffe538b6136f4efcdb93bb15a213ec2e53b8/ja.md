```
temporalprediction(U, em::AbstractSpatialEmbedding, tsteps; kwargs...)
```

`U::AbstractVector{<:AbstractArray{T, Φ}}`の形の時系列を用いて、`tsteps`回のスパティオ-テンポラル時系列予測を行います。ローカル加重モデリング[1]を使用します。

返されるデータは常に`U`の最終状態を出発点として含みます（返される全体の長さは`tsteps+1`です）。再構成プロセスは`em`によって定義されます。利用可能なメソッドとインターフェースについては[`AbstractSpatialEmbedding`](@ref)を参照してください。

## キーワード引数

  * `ttype = KDTree` : ツリー構造のタイプ/コンストラクタ。これまでのところ、`KDTree`でのみテストされています。
  * `method = AverageLocalModel(ω_safe)` : [`AbstractLocalModel`](@ref)のサブタイプ。
  * `ntype = FixedMassNeighborhood(3)` : `AbstractNeighborhood`のサブタイプ。
  * `initial_ts = U` : 予測の初期状態（`U`と同じタイプ）。使用される最大遅延時間と同じかそれ以上の状態を持っている必要があります。デフォルトはトレーニングセット`U`です。
  * `progress = true` : 進捗を表示するため。

## 説明

このメソッドは、[`localmodel_tsp`](@ref)と似たように機能し、遅延埋め込みの概念を空間的に拡張されたシステムに拡張します。システムの完全な状態を再構成する代わりに、ローカル状態が使用されます。埋め込みの詳細については[`AbstractSpatialEmbedding`](@ref)を参照してください。予測はフレームごとに、ポイントごとに実行されます。新しいフレームのすべての値が見つかると、そのフレームは時系列の末尾に追加され、次の時間ステップの新しい予測クエリを生成するために使用されます。

## パフォーマンスノート

埋め込みパラメータを選択する際は注意が必要です。メモリ使用量と計算時間は、結果として得られる埋め込み次元に強く依存します。

## 参考文献

[1] : U. Parlitz & C. Merkwirth, [Phys. Rev. Lett. **84**, pp 1890 (2000)](https://journals.aps.org/prl/abstract/10.1103/PhysRevLett.84.1890)
