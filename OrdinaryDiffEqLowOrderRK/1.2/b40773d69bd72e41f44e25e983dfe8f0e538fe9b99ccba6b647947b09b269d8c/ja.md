```julia
OwrenZen3(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。オウレン-ゼンナロ最適化補間3/2法（自由な3次補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: 適切なCPU配列での内部ブロードキャスティングが直列（`thread = OrdinaryDiffEq.False()`）で行われるか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。Juliaが複数のスレッドで起動されるとき。

## 参考文献

@article{owren1992derivation,     title={効率的で連続的な明示的ルンゲ–クッタ法の導出},     author={Owren, Brynjulf and Zennaro, Marino},     journal={SIAM journal on scientific and statistical computing},     volume={13},     number={6},     pages={1488–1501},     year={1992},     publisher={SIAM}     }
