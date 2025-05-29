```
changeHbasis(twoBodyInt::AbstractArray{T, 4}, 
             C1::AbstractMatrix{T}, C2::AbstractMatrix{T}) where {T} -> 
AbstractArray{T, 4}
```

入力の二体積分 `twoBodyInt` を、異なるスピン構成（例えば、制限のない場合）のための二つの軌道係数行列 `C1` と `C2` に基づいて基底を変更します。出力は3要素の `Tuple` で、最初の2つの要素はそれぞれのスピン構成の空間積分であり、最後の要素は異なるスピンを持つ軌道間のクーロン相互作用です。
