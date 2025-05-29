```
Nystrom4
```

4次の明示的ルンゲ-クッタ-ニーストローム法で、2次の常微分方程式に直接適用できます。固定時間ステップでのみ使用できます。

ODE問題が1次導関数に依存しない場合は、パフォーマンスを向上させるために[`Nystrom4VelocityIndependent`](@ref)の使用を検討してください。

## 参考文献

E. Hairer, S.P. Norsett, G. Wanner, (1993) Solving Ordinary Differential Equations I. Nonstiff Problems. 2nd Edition. Springer Series in Computational Mathematics, Springer-Verlag.
