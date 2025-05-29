```
hann_window(
    window_length::Int, ::Type{T} = Float32; periodic::Bool = true,
) where T <: Real
```

ハンウィンドウ関数 (参照: [ウィンドウ関数 § ハンおよびハミングウィンドウ - Wikipedia](https://en.wikipedia.org/wiki/Window_function#Hann_and_Hamming_windows))。

$$
w[n] = \frac{1}{2}[1 - \cos(\frac{2 \pi n}{N - 1})]
$$

ここで、$N$ はウィンドウの長さです。

```julia-repl
julia> lineplot(hann_window(100); width=30, height=10)
     ┌──────────────────────────────┐
   1 │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⣠⠚⠉⠉⠉⠢⡀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⡔⠁⠀⠀⠀⠀⠀⠘⢄⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⠀⢀⠞⠀⠀⠀⠀⠀⠀⠀⠀⠈⢆⠀⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⢀⡎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢣⠀⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⠀⠀⡎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢦⠀⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⠀⢀⠞⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢆⠀⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⠀⢀⡜⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢇⠀⠀⠀⠀⠀│
     │⠀⠀⠀⠀⢀⠎⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠈⢦⠀⠀⠀⠀│
     │⠀⠀⠀⢠⠊⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠣⡀⠀⠀│
   0 │⣀⣀⠔⠁⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠙⢤⣀│
     └──────────────────────────────┘
     ⠀0⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀100⠀
```

# 引数:

  * `window_length::Int`: ウィンドウのサイズ。
  * `::Type{T}`: ウィンドウの要素型。

# キーワード引数:

  * `periodic::Bool`: `true`（デフォルト）の場合、周期関数として使用するためのウィンドウを返します。`false` の場合、対称ウィンドウを返します。

    常に次が成り立ちます:

```jldoctest
julia> N = 256;

julia> hann_window(N; periodic=true) ≈ hann_window(N + 1; periodic=false)[1:end - 1]
true

julia> hann_window(N) ≈ hamming_window(N; α=0.5f0, β=0.5f0)
true
```

# 戻り値:

長さ `window_length` で型 `T` のベクトル。
