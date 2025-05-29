```
newton_raphson(func::Function, 
    u0::Union{Array,PyObject}, 
    θ::Union{Missing,PyObject, Array{<:Real}}=missing,
    args::PyObject...) where T<:Real
```

非線形方程式を解くためのニュートン・ラフソンソルバー。 ∘ `func` のシグネチャは 

  * `func(θ::Union{Missing,PyObject}, u::PyObject)->(r::PyObject, A::Union{PyObject,SparseTensor})` （`linesearch` がオフの場合）
  * `func(θ::Union{Missing,PyObject}, u::PyObject)->(fval::PyObject, r::PyObject, A::Union{PyObject,SparseTensor})` （`linesearch` がオンの場合）

ここで `r` は残差であり、`A` はヤコビ行列です。`linesearch` がオンの場合、関数値 `fval` も提供する必要があります。 ∘ `θ` は外部パラメータです。 ∘ `u0` は `u` の初期推定値です。 ∘ `args`: func 関数への追加入力 ∘ `kwargs`: `func` へのキーワード引数

解は `ADCME.options.newton_raphson` を介して構成できます。

  * `max_iter`: 最大反復回数（デフォルト=100）
  * `rtol`: 終了のための相対許容誤差（デフォルト=1e-12）
  * `tol`: 終了のための絶対許容誤差（デフォルト=1e-12）
  * `LM`: 浮動小数点数、レーベンバーグ・マルカート修正 $x^{k+1} = x^k - (J^k + \mu^k)^{-1}g^k$ （デフォルト=0.0）
  * `linesearch`: linesearch が使用されるかどうか（デフォルト=false）

現在、バックトレースアルゴリズムが実装されています。`linesearch` のパラメータは `options.newton_raphson.linesearch_options` を介して提供されます。

  * `c1`: 停止基準、$f(x^k) < f(0) + \alpha c_1  f'(0)$
  * `ρ_hi`: 新しいステップサイズ $\alpha_1\leq \rho_{hi}\alpha_0$
  * `ρ_lo`: 新しいステップサイズ $\alpha_1\geq \rho_{lo}\alpha_0$
  * `iterations`: linesearch の最大反復回数
  * `maxstep`: 許可される最大ステップ数
  * `αinitial`: ステップサイズ $\alpha$ の初期推定値

```
