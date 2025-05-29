```
remove_column!(F::UpdatableGivensQR, k::Int = size(F, 2))
```

行列の既存のQR因子分解`F`を、kᵗʰ列が削除された後の同じ行列の因子分解に更新します。計算の複雑さ: O(m^2) ただし size(F) = (n, m) です。
