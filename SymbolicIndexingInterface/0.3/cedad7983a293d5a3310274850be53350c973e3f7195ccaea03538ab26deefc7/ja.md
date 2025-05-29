```
struct ParameterTimeseriesCollection{T}
function ParameterTimeseriesCollection(collection)
```

複数のパラメータ時系列を保存するのに役立つユーティリティ構造体です。各時系列オブジェクトのコレクションを期待します（[`is_timeseries`](@ref)は[`Timeseries`](@ref)を返します）。各時系列オブジェクトは[`state_values`](@ref)と[`current_time`](@ref)を実装する必要があります。実質的に、含まれる各時系列オブジェクトの「状態」は、その時系列が保存するパラメータ値です。

コレクションは`Base.eachindex`、`Base.iterate`、および`Base.getindex`を実装することが期待されています。コレクションのインデックスは、対応するインデックスプロバイダーで[`timeseries_parameter_index`](@ref)を呼び出すことによって返される時系列インデックスと一致する必要があります。

この型は`eachindex`、`iterate`、および`length`を含まれる`collection`に転送します。含まれる`collection`へのアクセスを許可するために`Base.parent`を実装しており、以下の`getindex`メソッドを持っています：

  * `getindex(ptc::ParameterTimeseriesCollection, idx) = ptc.collection[idx]`。
  * `getindex(::ParameterTimeseriesCollection, idx::ParameterTimeseriesIndex)`は`idx`で参照されるパラメータの時系列を返します。
  * `getindex(::ParameterTimeseriesCollection, idx::ParameterTimeseriesIndex, subidx)`は`subidx`の時点で`idx`で参照されるパラメータの値を返します。
  * これらのケースを除いて、複数のインデックスが提供された場合、最初は時系列インデックスとして扱われ、2番目は時系列内の時間インデックス、（オプションの）3番目は時系列の要素内のパラメータのインデックスとして扱われます。

この型には[`parameter_values`](@ref)の三引数バージョンが実装されています。`parameter_values`の単一引数バージョンはキャッシュされたパラメータオブジェクトを返します。この型は特性を実装していません。
