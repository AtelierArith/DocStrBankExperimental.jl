```
lin_fun, simplified_sys = linearization_function(sys::AbstractSystem, inputs, outputs; simplify = false, initialize = true, initialization_solver_alg = TrustRegion(), kwargs...)
```

システム `sys` を線形化する関数を返します。関数 [`linearize`](@ref) は、より高レベルで使いやすいインターフェースを提供します。

`lin_fun` は関数 `(variables, p, t) -> (; f_x, f_z, g_x, g_z, f_u, g_u, h_x, h_z, h_u)` であり、すなわち、非線形 `sys`（技術的には `simplified_sys`）のためのヤコビ行列 `f,g,h` を持つ NamedTuple を返します。形式は次の通りです。

$$
\begin{aligned}
ẋ &= f(x, z, u) \\
0 &= g(x, z, u) \\
y &= h(x, z, u)
\end{aligned}
$$

ここで `x` は微分不明変数、`z` は代数変数、`u` は入力、`y` は出力です。線形状態空間表現を得るには、[`linearize`](@ref) を参照してください。入力引数 `variables` は動作点を定義するベクトルで、`unknowns(simplified_sys)` に対応し、`p` は `simplified_sys` のパラメータに対応するベクトルです。注意: `inputs` のすべての変数は `simplified_sys` のパラメータに変換されています。

`simplified_sys` は [`structural_simplify`](@ref) を経て、発生する入力または出力変数が引数 `inputs` と `outputs` で提供された変数に置き換えられています。このシステムの不明変数は、線形化された行列に対して保持される不明変数の順序も示しています。

# 引数:

  * `sys`: [`ODESystem`](@ref)。この関数は `sys` に自動的に簡略化パスを適用し、結果として得られる `simplified_sys` を返します。
  * `inputs`: 線形化された入出力モデルの入力を示す変数のベクトル。
  * `outputs`: 線形化された入出力モデルの出力を示す変数のベクトル。
  * `simplify`: テアリングで簡略化を適用します。
  * `initialize`: true の場合、動作点が一貫しているか（代数方程式を満たすか）を確認するチェックが行われます。一貫していない場合、初期化が行われます。
  * `initialization_solver_alg`: 指定された動作点を満たす状態および代数変数の実現可能なセットを解くために使用する非線形解法アルゴリズム。
  * `autodiff`: 必要なヤコビ行列を計算するために使用する DifferentiationInterface.jl によってサポートされる `ADType`。デフォルトは `AutoForwardDiff()` を使用します。
  * `kwargs`: `find_solvables!` に渡されます。

より高レベルのインターフェースを提供する [`linearize`](@ref) も参照してください。
