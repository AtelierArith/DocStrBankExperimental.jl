```
kernel_birkhoff(xs::AbstractArray, fs::AbstractVector, ϵ::Number, μ::Number;
                σ::Number=0., kernel::Symbol=:SquaredExponential,
                boundary_points::AbstractVector = [])
```

この関数は主に非推奨です。この問題の無限に離散化された限界（ビルコフ平均）の解は、ネイティブ空間には存在しません。したがって、結果は奇妙で解釈が難しく、揺れが生じることがあります。自己責任で使用してください。

カーネルアプローチを使用して関数の「ビルコフ平均」を求めます。最小二乗問題を解決します。

> `min_c μ⁻¹(‖GKc‖² + ‖Kc‖²_bd) + ϵ‖c‖²_k + ‖Kc - f‖²`


ここで

  * `‖GKc‖²` は不変性を罰するノルムです
  * `‖c‖²_k` はスムージングカーネルノルムです
  * `‖Kc - f‖²` は最小二乗フィットノルムです
  * `‖Kc‖²_bd` は境界違反を罰するノルムです

引数:

  * `xs`: サイズ d × 2N の補間点、ここで xs[:, N+1:2N] = F.(xs[:, 1:N])
  * `fs`: サイズ N の点での関数値
  * `ϵ`: 正則化の量（ゼロに設定可能）
  * `μ`: フィットのための不変性罰の重み（小さくするべき、例：1e-6）
  * `σ`: 問題のスケール
  * `kernel`: 補間するカーネルの種類（`KernelLabel`を参照）
  * `boundary_points`: 境界上の点のインデックスのリスト

出力:

  * `k`: KernelLabel オブジェクト

```
