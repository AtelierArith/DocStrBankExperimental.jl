```
normal(body::Body/BodyList[;axes=:inertial]) -> Tuple{Vector{Float64},Vector{Float64}}
```

現在の法線を慣性成分（`axes=:inertial`の場合）またはボディ固定成分（`axes=:body`の場合）で計算します。これは、ボディ`body`の周囲の面の法線であり、その端はボディの現在の`xend`および`yend`座標（慣性空間内）にあります。例えば、面1は点1と点2の間の面に対応します。`OpenBody`の場合、これはポイントの数よりも1要素短いベクトルを提供します。
