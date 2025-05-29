```
lossless_modes_dense(pso::PSOModel; min_freq::Real=0,
    max_freq::Union{Real, Nothing}=nothing)
```

損失を無視してPSOModelのモードを見つけるために、密なSVDソルバーを使用します。各モードは固有値 `λ` と固有ベクトル `v` で構成されます。モードの周波数は `imag(λ)/(2π)` であり、減衰率は `-2*real(λ)/(2π)` です。 `min_freq` と `max_freq` は固有値を見つける周波数範囲を指定します。
