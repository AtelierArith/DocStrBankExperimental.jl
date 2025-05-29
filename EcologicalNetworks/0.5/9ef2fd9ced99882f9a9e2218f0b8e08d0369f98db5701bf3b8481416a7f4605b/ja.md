```
make_joint_distribution(N::NT) where {NT<:AbstractEcologicalNetwork}
```

隣接行列または発生行列から計算された確率行列を返します。行列に負の値が含まれている場合はエラーを発生させます。出力はビット単位です。
