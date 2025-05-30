```
Nystrom4VelocityIdependent
```

4次の明示的ルンゲ・クッタ・ニーストローム法。加速度が速度に依存しない2次の常微分方程式（ODE）に直接使用されます（ODE問題は1次導関数に依存しません）。

速度に依存しない問題に対して[`Nystrom4`](@ref)よりも効率的で、必要な評価が少なくて済みます。

固定時間ステップのみ。

## 参考文献

E. Hairer, S.P. Norsett, G. Wanner, (1993) Solving Ordinary Differential Equations I. Nonstiff Problems. 2nd Edition. Springer Series in Computational Mathematics, Springer-Verlag.
