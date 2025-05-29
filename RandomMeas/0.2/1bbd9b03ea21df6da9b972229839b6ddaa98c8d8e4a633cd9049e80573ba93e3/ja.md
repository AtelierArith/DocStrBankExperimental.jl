```
`MeasurementData`オブジェクトを指定されたサブシステムに縮小し、利用可能な場合は測定設定タイプを保持します。

# 引数

  * `data::MeasurementData{T}`: 元の測定データオブジェクトで、`T`は`nothing`または`LocalMeasurementSetting`のサブタイプです。
  * `subsystem::Vector{Int}`: 保持するサブシステムを指定するサイトインデックスのベクター（1ベース）。各インデックスは1から`data.N`の間でなければなりません。

# 戻り値

  * 減少した測定結果を持つ新しい`MeasurementData{T}`オブジェクトで、次のようになります：
    * 次元が`(NM, N)`から`(NM, |subsystem|)`に縮小されます。
    * 減少した測定設定（提供されている場合）または`nothing`のまま残ります。

# 例

```

julia

# `data`がN = 4のMeasurementDataオブジェクトであるとします。

# サイト1と3のみを保持するには：

reduced*data = reduce*to_subsystem(data, [1, 3]) ```
