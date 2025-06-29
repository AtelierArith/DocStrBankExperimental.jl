```
ContinuousSpace(extent::NTuple{D, <:Real}; kwargs...)
```

範囲0から（ただし`extent`を含まない）`D`次元の`ContinuousSpace`を作成します。エージェントの位置（フィールド`pos`）は`SVector{D, <:Real}`型でなければならず、エージェントには`vel::SVector{D, <:Real}`フィールドを持たせることを強く推奨します。これは[`move_agent!`](@ref)と併用するためです。便利さのために[`ContinuousAgent`](@ref)を使用してください。

`ContinuousSpace`は、エージェントの位置、向き、速度が真の浮動小数点数である連続媒体上のエージェントダイナミクスの表現です。さらに、`ContinuousSpace`を含むモデル内で空間的特性を表現するためのサポートが提供されています。空間的特性（通常はモデルの特性に含まれる）は、位置ベクトルの関数`f(pos) = value`であるか、または解析的形式で利用できない空間データの離散化を表す`AbstractArrays`である可能性があります。後者の場合、位置は自動的に配列で表される離散化にマッピングされます。`ContinuousSpace`と併用して空間的特性にアクセスするには、[`get_spatial_property`](@ref)を使用してください。

さらに機能については、オンラインドキュメントの[`ContinuousSpace` exclusives](@ref ContinuosSpace_exclusives)も参照してください。連続空間を使用した例としては、[Flocking model](@ref)があります。

## 距離の指定

[`nearby_ids`](@ref)のような関数で指定された距離`r`は、`ContinuousSpace`内の2点間のユークリッド距離に基づいています。

`ContinuousSpace`では、`nearby_*`検索はグリッドシステムを使用して加速されます。以下のキーワード`spacing`に関する議論を参照してください。デフォルトでは、`nearby_*`のキーワード`search`は`:approximate`に設定されており、これは正確な検索を行わず、`r`をわずかに超えるエージェントIDを含む可能性のある過大評価を意味します。「わずかに」とは`spacing`の範囲内であることを指します。正確な検索を行いたい場合は、`nearby_*`のキーワード`search`を`:exact`に設定してください。

## キーワード

  * `periodic = true`: 空間が周期的かどうか。`false`に設定すると、エージェントの位置が境界を超えるとエラーが発生します。
  * `spacing::Real = minimum(extent)/20`: [`nearby_ids`](@ref)のような最近傍検索を加速するために使用される内部コンパートメントの間隔を設定します。コンパートメントは、エージェントが移動する`GridSpace`の完全なインスタンスです。`extent`内のすべての次元は、`spacing`で完全に割り切れる必要があります。`spacing`の値に最適な選択肢はなく、最適なパフォーマンスが必要な場合は、さまざまな選択肢に対してベンチマークを設定することをお勧めします。間隔が細かいほど、`nearby_ids`の不正確なバージョンはより速く、より正確になります。ただし、間隔が細かいほど、エージェントがコンパートメントをより頻繁に変更するため、`move_agent!`は遅くなります。
  * `update_vel!`: エージェントが移動する前にエージェントの速度を更新する**関数**`update_vel!(agent, model)`。もちろん、エージェントの相互作用中にエージェントの速度を変更することもできますが、`update_vel!`機能は、エージェントに個別に作用する空間的な力場（例：いくつかの磁場）を対象としています。`update_vel!`を使用する場合、エージェントタイプは`vel::SVector{D, <:Real}`フィールドを持っている必要があります。
