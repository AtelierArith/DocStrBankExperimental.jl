```
loadNeededPoints!(tsg::TasmanianSG, vals::Array{Float64})
```

必要な点でのターゲット関数の値を読み込みます。必要な点がない場合、現在読み込まれている値はリセットされます。

vals: 出力 X getNumNeeded() の次元を持つ配列。各列は、対応する必要な点での出力の値に対応します。順序と先頭の次元は、getNeededPoints() から取得した点と一致する必要があります。
