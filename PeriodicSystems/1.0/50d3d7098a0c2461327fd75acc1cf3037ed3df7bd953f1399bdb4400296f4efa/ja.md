```
pslinfnorm(psys, K = 100; hinfnorm = false, rtolinf = 0.001, offset = sqrt(ϵ), reltol, abstol, dt) -> (linfnorm, fpeak)
pshinfnorm(psys, K = 100; rtolinf = 0.001, offset = sqrt(ϵ), reltol, abstol, dt) -> (linfnorm, fpeak)
```

連続時間周期システム `psys = (A(t),B(t),C(t),D(t)` の `L∞` ノルム `linfnorm` を `pslinfnorm` で、または `H∞` ノルム `hinfnorm` を `pshinfnorm` で計算します [1]。 `hinfnorm = true` の場合、`H∞` ノルムは `pslinfnorm` で計算されます。ピークゲインが達成されるピーク周波数 `fpeak` は通常決定されませんが、いくつかの制限ケースを除きます。 `L∞` ノルムは、`psys` が虚軸上に極を持つ場合は無限大になります。

虚軸上に極がないことを確認するために、`A(t)` の特性指数は、実部が区間 `[-β,β]` にない必要があります。ここで、`β` は安定性領域の境界オフセットです。使用するオフセット `β` は、キーワードパラメータ `offset = β` を介して指定できます。`β` に使用されるデフォルト値は `sqrt(ϵ)` で、ここで `ϵ` は作業用の機械精度です。

[2] に記載されているように、二分法に基づくアルゴリズムが `L∞` ノルムを近似するために使用され、キーワード引数 `rtolinf` は計算された無限ノルムの相対精度を指定します。`rtolinf` に使用されるデフォルト値は `0.001` です。

`hinfnorm = true` の場合、`H∞` ノルムが計算されます。この場合、システムの安定性も追加でチェックされ、安定していないシステムの場合、`H∞` ノルムは無限大になります。安定性を確認するために、`A(t)` の特性指数は実部が `-β` より小さい必要があります。

システムハミルトニアンの特性乗数を計算するために使用されるODEソルバーは、キーワード引数 `solver` を使用して指定できます（デフォルト: `solver = "symplectic"`）と、必要な相対精度 `reltol`（デフォルト: `reltol = 1.e-4`）、絶対精度 `abstol`（デフォルト: `abstol = 1.e-7`）、およびステップサイズ `dt`（デフォルト: `dt = 0`）です。ステップサイズの値は、`solver = "symplectic"` の場合にのみ関連し、この場合 `dt = 0` の場合は適応的なステップサイズ戦略が使用され、`dt > 0` の場合は固定ステップサイズが使用されます。希望する相対精度 `reltol` に応じて、`reltol >= 1.e-4` の場合は低次のソルバーが使用され、一般的に非常に効率的ですが、精度は低くなります。`reltol < 1.e-4` の場合は、高精度の要求に対応できる高次のソルバーが使用されます。

次のソルバーは、[OrdinaryDiffEq.jl](https://github.com/SciML/OrdinaryDiffEq.jl) パッケージから選択できます：

`solver = "non-stiff"` - 非剛性問題用のソルバーを使用します（`Tsit5()` または `Vern9()`）;

`solver = "stiff"` - 剛性問題用のソルバーを使用します（`Rodas4()` または `KenCarp58()`）;

`solver = "linear"` - 固定時間ステップ `dt` の線形ODE用の特別なソルバーを使用します（`MagnusGL6()`）;

`solver = "symplectic"` - シンプレクティックハミルトニアン構造を保持するソルバーを使用します（`IRKGL16()`）;

`solver = "auto"` - デフォルトのソルバーを使用し、剛性問題を自動的に検出します（`AutoTsit5(Rosenbrock23())` または `AutoVern9(Rodas5())`）。

*参考文献:*    

[1] P. Colaneri. Continuous-time periodic systems in H2 and H∞: Part I: Theoretical Aspects.     Kybernetika, 36:211-242, 2000. 

[2] A. Varga, On solving periodic differential matrix equations with applications to periodic system norms computation.     Proc. CDC/ECC, Seville, p.6545-6550, 2005.  
