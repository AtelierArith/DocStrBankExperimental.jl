```
relativeionizationcrosssection(z::Int, ss::Int, ev::AbstractFloat)
relativeionizationcrosssection(ass::AtomicSubShell, ev::AbstractFloat, ::Type{Pouchou1991})
```

PouchouとPouchoirの1991年（グリーンブック）の表現に基づくイオン化断面積の近似式と、サブシェルの占有に対する追加の因子。

例:

```
> (/)(map(e->NeXLCore.relativeionizationcrosssection(n"Fe K",e),[10.0e3,20.0e3])...)
0.5982578301818324
```
