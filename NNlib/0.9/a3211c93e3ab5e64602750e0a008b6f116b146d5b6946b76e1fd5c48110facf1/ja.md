```
hamming_window(
    window_length::Int, ::Type{T} = Float32; periodic::Bool = true,
    α::T = T(0.54), β::T = T(0.46),
) where T <: Real
```

ハミング窓関数 (参照: [ウィンドウ関数 § ハンとハミング窓 - Wikipedia](https://en.wikipedia.org/wiki/Window_function#Hann_and_Hamming_windows))。`hann_window`の一般化されたバージョンです。

$$
w[n] = \alpha - \beta \cos(\frac{2 \pi n}{N - 1})
$$

ここで、$N$はウィンドウの長さです。

```julia-repl
julia> lineplot(hamming_window(100); width=30, height=10)
     ┌──────────────────────────────┐
   1 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡠⠚⠉⠉⠉⠢⡄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠎⠁⠀⠀⠀⠀⠀⠈⢢⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⢠⠊⠀⠀⠀⠀⠀⠀⠀⠀⠀⢣⡀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⢰⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠱⡀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⣠⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠳⡀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⢰⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠱⡄⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⡰⠃⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠱⡀⠀⠀⠀⠀│
     │⠀⠀⠀⢀⠴⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠘⢄⠀⠀⠀│
     │⠀⢀⡠⠊⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠳⣀⠀│
   0 │⠉⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉│
     └──────────────────────────────┘
     ⠀0⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀100⠀
```

# 引数:

  * `window_length::Int`: ウィンドウのサイズ。
  * `::Type{T}`: ウィンドウの要素型。

# キーワード引数:

  * `periodic::Bool`: `true`（デフォルト）の場合、周期関数として使用するためのウィンドウを返します。`false`の場合、対称ウィンドウを返します。

    常に次が成り立ちます:

```jldoctest
julia> N = 256;

julia> hamming_window(N; periodic=true) ≈ hamming_window(N + 1; periodic=false)[1:end - 1]
true
```

  * `α::Real`: 上記の式における係数α。
  * `β::Real`: 上記の式における係数β。

# 戻り値:

長さ`window_length`、要素型`T`のベクトル。
