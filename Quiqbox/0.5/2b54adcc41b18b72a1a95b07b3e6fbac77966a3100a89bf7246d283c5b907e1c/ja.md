```
eeInteraction(bf1::AbstractGTBasisFuncs{T, D, 1}, 
              bf2::AbstractGTBasisFuncs{T, D, 1}, 
              bf3::AbstractGTBasisFuncs{T, D, 1}, 
              bf4::AbstractGTBasisFuncs{T, D, 1}) where {T, D} -> 
T
```

4つの基底関数（化学者の表記で順序付けられた）を与えられたときに、電子-電子相互作用テンソル要素を返します。
