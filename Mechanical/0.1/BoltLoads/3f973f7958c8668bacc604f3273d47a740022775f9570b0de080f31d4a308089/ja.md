```
bolt_loads(points; Fc=[0,0,0]N, Mc = [0,0,0]N*m, A=1mm^2, udf_pivot=false, length_format = "mm", load_format = "kN", return_plot_data=false)
```

ボルトパターンの重心に作用する力とモーメントに対するボルト荷重を計算します。

`points`はxおよびy座標のタプル（[x], [y]）です。`points`は関数[`circle`](@ref)および[`rectangle`](@ref)によって生成される場合があります。`Fc`はボルトパターンの重心で作用する力をベクトル[Fxc, Fyc, Fzc]として入力します。`Mc`はボルトパターンの重心で作用するモーメントをベクトル[Mxc, Myc, Mzc]として入力します。`udf_pivot`は計算されるときはfalseで、特定のピボットポイントを手動で入力したい場合は[x,y]として入力されます。`A`はボルトの応力面積で、すべてのボルトに対して単一の値として入力するか、各ボルトに対して異なる値（すなわちベクトル）として入力します。`length_format`は'mm'、`cm`、'm`または`inch`のいずれかで、返される表示出力を設定します。`load_format`は'N'、'kN'、または`lbf`で、返される表示出力を設定します。`Unitful`パッケージに準拠した単位が適用されるべきです。

# 例

```julia-repl
julia> using Unitful: mm, m, N
julia> p = x, y = circle(r=100mm, N=7);
julia> Fc = [7000, 7000, 5000]N;
julia> Mc = [30_000, 20_000, 15_000]N*m;
julia> bolt_loads(p, Fc=Fc, Mc=Mc)
7×4 DataFrame
 Row │ x               y            Paxial       Pshear     
     │ Quantity…       Quantity…    Quantity…    Quantity…  
─────┼──────────────────────────────────────────────────────
   1 │ 6.12323e-15 mm     100.0 mm   86.4286 kN   20.453 kN
   2 │     78.1831 mm    62.349 mm   9.48018 kN  21.6326 kN
   3 │     97.4928 mm  -22.2521 mm  -74.0691 kN  22.6385 kN
   4 │     43.3884 mm  -90.0969 mm  -101.305 kN  22.7682 kN
   5 │    -43.3884 mm  -90.0969 mm  -51.7183 kN  21.9363 kN
   6 │    -97.4928 mm  -22.2521 mm   37.3512 kN  20.7108 kN
   7 │    -78.1831 mm    62.349 mm   98.8324 kN  20.0239 kN
```
