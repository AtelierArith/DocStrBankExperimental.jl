```
quat2viewer(q::QuatRotation)
quat2viewer(rot::AbstractMatrix)
quat2viewer(orient::AbstractVector)
```

クォータニオン q をビューワー参照フレームに変換します。これは回転行列または 4 要素のベクトル [w,i,j,k] として渡すこともでき、ここで w は実部、i、j、k はクォータニオンの虚部です。
