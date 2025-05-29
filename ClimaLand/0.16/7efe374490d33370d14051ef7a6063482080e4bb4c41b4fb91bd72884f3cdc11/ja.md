```
total_energy_per_area!(
    surface_field,
    land::AbstractLandModel,
    Y,
    p,
    t,
    sfc_cache,
```

)

単位面積あたりの総エネルギーを計算し、コンポーネントモデルのために同じ関数を呼び出すことによって、土地モデル `land` の `surface_field` をその場で更新する関数です。

`sfc_cache` フィールドはスクラッチスペースとして利用可能です。
