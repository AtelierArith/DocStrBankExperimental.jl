```
sceua(fn::Function, x0::Vector, bl::Vector, bu::Vector;
    maxn=500, kstop=5, pcento=0.01, peps=0.001, ngs=5, iseed=-1, iniflg=1)
```

# 戻り値:

`bestx, bestf, exitflag, output`

# 例:

```julia
x, feval, exitflag, output = sceua(fn, x0, bl, bu)
```
