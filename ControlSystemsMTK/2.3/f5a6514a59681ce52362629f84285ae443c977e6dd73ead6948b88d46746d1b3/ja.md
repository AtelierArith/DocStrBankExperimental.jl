```
GainScheduledStateSpace(systems, vt; interpolator, x = zeros((systems[1]).nx), name, u0 = zeros((systems[1]).nu), y0 = zeros((systems[1]).ny))
```

線形パラメータ変動（LPV）バージョンの [`Blocks.StateSpace`](@ref) で、以下の方程式を実装しています：

$$
\begin{aligned}
\dot{x} &= A(v) x + B(v) u \\
y        &= C(v) x + D(v) u
\end{aligned}
$$

ここで `v` はスカラーのスケジューリング変数です。

[ゲインスケジューリングの例](https://juliacontrol.github.io/ControlSystemsMTK.jl/dev/batch_linearization/#Gain-scheduling) での使用例を参照してください。

# 引数：

  * `systems`: `ControlSystemsBase.StateSpace` オブジェクトのベクター
  * `vt`: スケジューリング変数 `v` のためのブレークポイント値のベクターで、これは `systems` と同じ長さです。
  * `interpolator`: コンストラクタ `i = interpolator(values, breakpoints)` で、`i(v)` のように呼び出すことができる補間オブジェクトを返します。DataInterpolations.jl の `LinearInterpolation` は良い選択ですが、ルックアップテーブルも使用できます。

# コネクタ

  * `input` 型 `RealInput` は $u$ に接続します。
  * `output` 型 `RealOutput` は $y$ に接続します。
  * `scheduling_input` 型 `RealInput` は $v$ に接続します。
