```
getDetectors(detectors_array::Vector{<:Detector} = Detector[])::Vector{Detector}
```

入力された検出器に基づいて、`detectors_array`をVector{Detector}として返し、検出器の体積に従ってソートします。ユーザーに`console`から検出器のパラメータを入力するよう促します。

!!! note
    入力に配列が受け取られなかった場合、変換された検出器を受け取るために空の配列が作成されます。

