```
flux_nonconservative_ersing_etal(u_ll, u_rr, orientation, equations::ShallowWaterExnerEquations1D)
```

非対称パス保存型の二点フラックスで、流体層の静水圧と堆積層からの追加圧力寄与を含む[`ShallowWaterExnerEquations1D`](@ref)の非保守項を離散化し、エントロピー不等式を得るものです。

この非保守フラックスは、エントロピー保存かつバランスの取れたスキームを作成するために、[`flux_ersing_etal`](@ref)と一緒に使用する必要があります。
