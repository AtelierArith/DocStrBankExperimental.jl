```
random_mps(sites::Vector{<:Index}, state; linkdims=1)
```

リンク次元 `linkdims` を持つ実際のランダム MPS を構築します。これは、`state` によって指定された初期の積状態をランダム化することによって作成されます。このバージョンの `random_mps` は、QNITensors からなる QN 保存のランダム MPS を作成する際に必要です。提供された初期の `state` 配列は、結果として得られるランダム MPS の総 QN を決定します。
