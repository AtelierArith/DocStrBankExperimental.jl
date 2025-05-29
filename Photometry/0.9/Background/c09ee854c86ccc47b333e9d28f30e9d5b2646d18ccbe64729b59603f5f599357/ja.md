```
sigma_clip(x, sigma; fill=:clamp, center=median(x), std=std(x, corrected=false))
sigma_clip(x, sigma_low, sigma_high; fill=:clamp, center=median(x), std=std(x, corrected=false))
```

この関数は、入力 `x` のシグマクリップされた値を返します。

上限と下限を `sigma_low` と `sigma_high` で指定します。そうでなければ、これらは等しいと仮定されます。`center` と `std` は、中央要素と標準偏差を求めるための関数であるオプションのキーワード引数です。

`fill === :clamp` の場合、これは `center - sigma_low * std` より小さい `x` の値と、`center + sigma_high * std` より大きい値をクリップします。それ以外の場合、これらの値は `fill` で置き換えられます。

# 例

```jldoctest
julia> x = randn(100_000);

julia> extrema(x)
(-4.496308951466683, 4.080724496910187)

julia> x_clip = sigma_clip(x, 1);

julia> extrema(x_clip) # おおよそ (-1, 1) であるべき
(-1.0042721545326967, 0.9957463910682249)
```
