```
bisect_to_edge(pds::ParallelDynamicalSystem, mapper::AttractorMapper; kwargs...) -> u1, u2
```

2つの状態 `u1, u2 = current_states(pds)` の間の流域境界を位相空間内の直線に沿って二分することによって見つけます。状態 `u1` と `u2` は異なる流域に属している必要があります。

三つ組 `u1, u2, success` を返します。ここで `u1, u2` は流域境界の両側に位置し、互いに `bisect_thresh`（状態空間におけるユークリッド距離）未満の距離にある2つの新しい状態であり、`success` は二分が成功したかどうかを示すBoolです（`mapper` が両方の状態を同じアトラクタの流域にマッピングする場合、失敗する可能性があり、その場合は警告が発生します）。

## キーワード引数

  * `bisect_thresh = 1e-7`: 返される2つの状態間の最大（ユークリッド）距離。

## 説明

`pds` は2つの状態を持つ `ParallelDynamicalSystem` です。`mapper` は `AttractorsViaProximity` または `AttractorsViaRecurrences` のサブタイプの `AttractorMapper` でなければなりません。

!!! info
    `u1` と `u2` の間の直線が流域境界と複数回交差する場合、このメソッドはこれらの交差点の1つを見つけます。アトラクタが2つ以上存在する場合、返される2つの状態のうちの1つは初期条件 `u1` と `u2` とは異なる流域に属する可能性があります。二分が第三の流域を含む場合は警告が発生します。

