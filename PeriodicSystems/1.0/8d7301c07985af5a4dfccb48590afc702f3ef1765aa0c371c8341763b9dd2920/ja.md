```
pdlqofc_sw(psys, Q, R, ns; S, vinit, kwargs...) -> (Fopt, info)
```

離散時間周期状態空間システム `psys = (A(t),B(t),C(t),D(t))` の形で計算します

x(t+1) = A(t)x(t) + B(t)u(t) + Bw(t)w(t)       y(t) = C(t)x(t) + D(t)u(t) + Dw(t)w(t) ,

出力フィードバック制御則における最適スイッチング周期フィードバックゲイン `Fopt(t)` を  

```
u(t) = Fopt(t)*y(t),
```

期待値の二次指標 

```
 J = E{ Sum [x(t)'*Q(t)*x(t) + 2*x(t)'*S(t)*u(t) + u(t)'*R(t)*u(t)] },
```

を最小化します。ここで `Q(t)`、`R(t)` および `S(t)` は周期的重み行列です。制御入力 `u(t)` に `m`、測定可能な出力 `y(t)` に `p` の順序 `n` のシステムの場合、`Q(t)` と `R(t)` はそれぞれ `n×n` および `m×m` の対称周期行列であり、`S(t)` はキーワード引数 `S` を介して指定できる `n×m` の周期行列です。デフォルトでは `S = missing` であり、その場合 `S(t) = 0` と仮定されます。周期行列 `Q(t)`、`R(t)` および `S(t)` は状態空間システムの行列と同じ型、すなわち `PeriodicMatrix` または `PeriodicArray` のいずれかです。`u(t)` の次元 `m` は `R(t)` の次元から推測されます。`Q`、`R` および `S` は定数実行列として代わりに提供することもできます。

得られるスイッチング周期ゲイン `Fopt(t)` のスイッチング時間は `N` 次元の整数ベクトル `ns` によって指定されます。デフォルトでは `ns = 1:N` であり、ここで `N` は最大サンプル数（すなわち `N = psys.period/psys.Ts`）です。

得られる `m×p` の周期出力フィードバックゲイン `Fopt(t)` は `SwitchingPeriodicArray` 型であり、次のように計算されます `Fopt(t) = inv(I+F(t)D(t))*F(t)`、ここで `F(t)` は次のように定義されます 

```
 F(t) = F_i for t ∈ [ns[i]Δ,ns[i+1]Δ) and i ∈ {1, ..., N-1}, or
 F(t) = F_N for t ∈ [ns[N]Δ,T),
```

ここで `T` はシステムの周期（すなわち `T = psys.period`）、`Δ` はシステムのサンプリング時間（すなわち `Δ = psys.Ts`）であり、`F_i` は `i` 番目のゲインです。

最適化変数 `v` の初期値がキーワード引数 `vinit = gains` を使用して提供される場合、`gains` は `m×p×N` の配列でなければなりません。ここで `m` と `p` はシステムの制御入力と出力の数です。デフォルトでは `vinit = missing` であり、その場合ゼロ行列 `gains = 0` が仮定されます。

`kwargs` に含まれる他のキーワード引数は、関数 [`pdlqofc`](@ref) に使用されるものと同じです。すべてのキーワード引数の説明については、そのドキュメントを参照してください。

勾配の計算は、フィードバックゲインのスイッチング構造を完全に活用し、[1] で考慮された定常フィードバックのケースを一般化する式を使用します。

*参考文献*     

[1] A. Varga and S. Pieters. Gradient-based approach to solve optimal periodic output feedback problems.      Automatica, vol.34, pp. 477-481, 1998.
