```
regions(f::Vector{Expression})
regions(f::System)
```

ハイパーサーフェスのリスト 'f = [f*1,...f*k]' を入力します。出力は、ハイパーサーフェス配置の補集合における領域、その符号パターン、オイラー特性、および各領域における臨界点のインデックスです。

オプション:

  * `bounded_check = false`: true の場合、アルゴリズムは領域が有界か無限大かも計算します。
  * `projective_fusion = false`: `true` の場合、アルゴリズムはどの領域が無限大で融合しているかを計算します。
  * `target_parameters`: [System](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/systems/) `f` のパラメータを指定します（もしあれば）。
  * `show_progress = true`: true の場合、計算の進行状況をターミナルに表示します。
  * `s`: モース関数 `f_1^(s_1) * ... * f_k^(s_k) * q^(s_k+1)` の指数。ここで、`s` は整数のリスト `[s_1, ..., s_k, s_{k+1}]` であり、`s_1, ..., s_k>0, s_{k+1}<0` かつ `2 s_{k+1} > s_1 deg(f_1) + ... + s_k deg(f_k)` です。
  * `epsilon = 1e-6`: 各臨界点からどれだけ近くでパス追跡を行うか。
  * `reltol = 1e-6`, `abstol = 1e-9`: ODE ソルバーの精度に関するパラメータ。
  * `monodromy_options = MonodromyOptions(max_loops_no_progress = 25)`: [モノドロミー](https://www.juliahomotopycontinuation.org/HomotopyContinuation.jl/stable/monodromy/) のオプションを渡します。
  * `start_pair_using_newton::Bool = false`: true の場合、アルゴリズムはニュートン法を使用してモノドロミーのためのスタートペアを計算しようとします。臨界点の数を減らすことができますが、安定性は低下します。

`bounded_check = true` の場合のオプション:

  * `δ::Float64 = 1e-8`: 無限大の周りの帯域を定義するパラメータ。

## 例

```julia
using HypersurfaceRegions
@var x y
f = [x^2 + y^2 - 1; x^2 + y^2 - 4];
regions(f)
```

## 有界性に関する情報を含む例

```julia
regions(f; bounded_check = true)
```
