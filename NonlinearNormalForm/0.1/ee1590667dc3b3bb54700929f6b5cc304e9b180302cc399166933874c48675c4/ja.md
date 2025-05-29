```
log!(F::VectorField, m1::DAMap; work::Tuple{DAMap,DAMap,DAMap,VectorField,VectorField}=prep_log_work(m1), work_Q::Union{Quaternion,Nothing}=prep_work_Q(F))
```

マップ `m1` の対数を計算します。つまり、マップ `m1` をリー指数 `exp(F)` として表す `VectorField` `F` を計算し、その結果を `F` に格納します。この収束が速くなるためには、マップ `m1` は単位に近い必要があります。

### キーワード引数

  * `work` – `m1` と同じ型の 3 つの `DAMap` と 2 つの `VectorField` のタプル
  * `work_Q`   – ベクトルフィールドにスピンが含まれている場合は `Quaternion{T}`、そうでなければ `nothing`
