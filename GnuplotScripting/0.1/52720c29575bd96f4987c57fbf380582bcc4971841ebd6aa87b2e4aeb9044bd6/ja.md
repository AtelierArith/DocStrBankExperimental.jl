```julia
free_form(gp::GnuplotScript,gp_line::AbstractString)
```

gnuplotコマンドを書く。このコマンドラインは直接Gnuplotに転送される。唯一の違いは、最初のプロットでも`replot`を使用できることだ。これはプロットを連鎖させるときに便利で、現在のコマンドが最初のプロットであるかどうかを心配する必要がない。

# 使用例

```julia
using GnuplotScripting

gp = GnuplotScript()

free_form(gp, "replot sin(x) lw 2 t 'a trigonometric function'")
```
