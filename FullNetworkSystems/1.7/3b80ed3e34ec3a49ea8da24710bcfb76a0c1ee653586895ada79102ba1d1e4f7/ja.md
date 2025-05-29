```
compute_ptdf(system::System; block_size, reference_bus_index) -> KeyedArray
compute_ptdf(buses::Buses, branches::Branches; block_size, reference_bus_index) -> KeyedArray
```

システムまたはそのシステムのデータを受け取り、`M` ブランチ、`N` バスのグリッドを表し、ネットワークの `M * N` DC-パワー伝達分配係数 (DC-PTDF) 行列を返します。

約15,000バスのシステムで集約された境界を持つ場合、これは約1分かかると予想されます。

# キーワード

  * `block_size=13_000`: 大きな行列を逆行列化するために分割する際に使用されるブロックサイズ。
  * `reference_bus=first(keys(buses))`: 参照バスの名前。

# 出力

  * `::KeyedArray`: PTDF行列; 軸にはブランチとバスの名前が含まれます。

!!! note
    入力データには孤立したコンポーネントや島が含まれてはいけません。

