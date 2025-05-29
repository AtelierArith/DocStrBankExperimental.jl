```
WolfePowellLinesearch <: Linesearch
```

バックトラッキングラインサーチを行い、点 $x$ からの探索方向 $η$ に沿ってウルフ条件を満たすステップサイズ $α$ を見つけます。

$$
f\bigl( \operatorname{retr}_x(αη) \bigr) ≤ f(x_k) + c_1 α_k ⟨\operatorname{grad}f(x), η⟩_x
\quad\text{および}\quad
\frac{\mathrm{d}}{\mathrm{d}t} f\bigr(\operatorname{retr}_x(tη)\bigr)
\Big\vert_{t=α}
≥ c_2 \frac{\mathrm{d}}{\mathrm{d}t} f\bigl(\operatorname{retr}_x(tη)\bigr)\Big\vert_{t=0}.
$$

# コンストラクタ

2つのコンストラクタが存在し、最初の（オプションの）パラメータとして多様体 `M` が提供されると、そのデフォルトの再収束とベクトル輸送がデフォルトになります。この場合、再収束とベクトル輸送も使いやすさのためにキーワード引数として指定できます。もう一つのコンストラクタは後方互換性のために保持されています。`stop_when_stepsize_less` は、ステップサイズが小さすぎる場合に停止するためのもので、新しいシグネチャに `M` を含む場合のみ利用可能です。

```
WolfePowellLinesearch(M, c1::Float64=10^(-4), c2::Float64=0.999; kwargs...
```

Wolfe-Powellラインサーチを生成します。

## キーワード引数

  * `candidate_point`:         (`allocate_result(M, rand)`) 候補のためのメモリ
  * `candidate_tangent`:       (`allocate_result(M, zero_vector, candidate_point)`) 勾配のためのメモリ
  * `candidate_direcntion`:    (`allocate_result(M, zero_vector, candidate_point)`) 方向のためのメモリ
  * `max_stepsize`:            ([`max_stepsize`](@ref)`(M, p)`) ここで許可される最大ステップサイズ。
  * `retraction_method`:       (`ExponentialRetraction()`) 使用する再収束
  * `stop_when_stepsize_less`: (`0.0`) 停止する最小ステップサイズ（最後のものが取られます）
  * `vector_transport_method`: (`ParallelTransport()`) 使用するベクトル輸送法
