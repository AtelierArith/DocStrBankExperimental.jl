```julia
gp = GnuplotScript(;direct_plot = true)
```

gnuplot スクリプト `gp` を作成します。`direct_plot` が true の場合、登録された操作を同時にプロットします。

# 使用例

次のように簡単なプロットを行うことができます：

```julia
gp = GnuplotScript(;direct_plot = true)

X=[-pi:0.1:pi;];
Ys = sin.(X);
Yc = cos.(X);

id = register_data(gp,hcat(X,Ys,Yc))
free_form(gp,"replot '$id' u 1:3 w l t 'cos'")
free_form(gp,"replot '$id' u 1:2 w l t 'sin'")
```

プロットはすぐに作成されます。

# 参照

  * [`register_data`](@ref)
  * [`free_form`](@ref)
