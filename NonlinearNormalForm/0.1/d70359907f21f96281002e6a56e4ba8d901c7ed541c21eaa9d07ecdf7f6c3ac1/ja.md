```
mul!(m::DAMap, F::VectorField, m1::DAMap; work_Q::Union{Quaternion,Nothing}=prep_work_Q(F))
```

`DAMap` `m1` に作用する Lie 演算子 `F` を計算し、その結果を `m` に格納します。具体的には、`F * m = (F.x, F.Q) * (m.x, m.Q) = (F.x ⋅ ∇ m.x , F.x ⋅ ∇ m.Q + m.Q*F.Q)` です。

### キーワード引数 - `work_Q`   – ベクトル場にスピンが含まれている場合は `Quaternion{T}`、そうでない場合は `nothing`
