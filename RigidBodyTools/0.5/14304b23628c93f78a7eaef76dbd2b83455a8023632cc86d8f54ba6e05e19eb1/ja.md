```
normal(body::Body/BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

現在の法線を計算します。これは、`axes=:inertial`の場合は慣性成分、`axes=:body`の場合はボディ固定成分です。ボディ`body`の周囲の面の法線を計算します。これらの面は、ボディの現在の`xend`および`yend`座標（慣性空間内）にある端点に対応しています。例えば、面1は点1と点2の間の面に対応します。`OpenBody`の場合、これはポイントの数よりも1要素短いベクトルを提供します。
