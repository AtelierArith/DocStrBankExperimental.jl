```
getDetectors(detector_info_array::Matrix{<:Real}, 
				 detectors_array::Vector{<:Detector} = Detector[]; 
				 						   console_FB=true)::Vector{Detector}
```

`detectors_array`をVector{Detector}として返しますが、成功裏に変換された検出器で拡張します。一方、`detector_info_array`の情報から検出器の変換を試みます。

!!! 注     `console_FB`引数がtrueに設定されている場合、`detector_info_array`が空であるか数値要素を含まない場合、関数は`getDetectors()`を呼び出して`console`から入力を受け取ります。
