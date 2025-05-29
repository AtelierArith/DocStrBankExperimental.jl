```
quat2euler(q::QuatRotation)
quat2euler(q::AbstractVector)
```

クォータニオンをラジアン単位のロール、ピッチ、ヨー角に変換します。クォータニオンは4要素のベクトル（w, i, j, k）またはQuatRotationオブジェクトであることができます。
