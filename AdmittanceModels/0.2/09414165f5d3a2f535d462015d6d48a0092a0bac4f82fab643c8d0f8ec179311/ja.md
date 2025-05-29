```
lossy_modes_dense(pso::PSOModel; min_freq::Real=0,
    max_freq::Union{Real, Nothing}=nothing, real_tol::Real=Inf, imag_tol::Real=Inf)
```

PSOModelの減衰モードを見つけるために、密な固有値ソルバーを使用します。各モードは、固有値 `λ` と空間分布ベクトル `v` で構成されます。モードの周波数は `imag(λ)/(2π)` であり、減衰率は `-2*real(λ)/(2π)` です。 `min_freq` と `max_freq` は、固有値を見つける周波数範囲を指定します。受動性は逆冪法ソルバーを使用して強制され、 `real_tol` と `imag_tol` は、固有値の実部と虚部の収束を決定するためにその方法で使用される許容誤差です。
