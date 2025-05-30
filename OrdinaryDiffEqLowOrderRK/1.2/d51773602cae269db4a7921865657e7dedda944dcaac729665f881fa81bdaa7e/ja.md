```julia
OwrenZen5(; stage_limiter! = OrdinaryDiffEq.trivial_limiter!,
            step_limiter! = OrdinaryDiffEq.trivial_limiter!,
            thread = OrdinaryDiffEq.False())
```

明示的ルンゲ-クッタ法。オーレン-ゼンナロ最適化補間5/4法（自由な5次補間子）。

### キーワード引数

  * `stage_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `step_limiter!`: 形式 `limiter!(u, integrator, p, t)` の関数
  * `thread`: Juliaが複数のスレッドで起動されたときに、適切なCPU配列での内部ブロードキャストを直列（`thread = OrdinaryDiffEq.False()`）にするか、複数のスレッドを使用するか（`thread = OrdinaryDiffEq.True()`）を決定します。

## 参考文献

@article{owren1992derivation,     title={効率的で連続的な明示的ルンゲ–クッタ法の導出},     author={Owren, Brynjulf and Zennaro, Marino},     journal={SIAM journal on scientific and statistical computing},     volume={13},     number={6},     pages={1488–1501},     year={1992},     publisher={SIAM}     }
