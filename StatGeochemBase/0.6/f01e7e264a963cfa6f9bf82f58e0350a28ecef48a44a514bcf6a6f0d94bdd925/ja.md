```julia
draw_from_distribution!(x::DenseArray{<:AbstractFloat}, dist::Collection{AbstractFloat})
```

既存の変数 `x` に、PDF曲線を定義するベクトル `dist` によって指定された連続確率分布から引き出されたランダムな浮動小数点数を埋め込みます。
