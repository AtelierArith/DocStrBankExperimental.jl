```
ff_controller(l::LQGProblem, L = lqr(l), K = kalman(l))
```

フィードフォワードコントローラ $C_{ff}$ を返します。これは参照をプラント入力にマッピングします: $u = C_{fb}y + C_{ff}r$

次の条件が成り立つ必要があります。

```
Cff = RobustAndOptimalControl.ff_controller(l)
Cfb = observer_controller(l)
Gcl = feedback(system_mapping(l), Cfb) * Cff # 注意: feedbackのカンマ、P/(I + PC) * Cff
dcgain(Gcl) ≈ I # またはIに似た非正方行列
```

[`extended_controller`](@ref) が使用される場合、上記のDCゲイン補償は使用できません。[`extended_controller`](@ref) は、参照が `u = L(xᵣ - x̂)` のように入ることを前提としています。

[`observer_controller`](@ref) も参照してください。
