```
runcircuit(hilbert::Vector{<:Index}, circuit::Vector;
           full_representation::Bool = false,
           process::Bool = false,
           noise = nothing,
           kwargs...)

runcircuit(M::Union{MPS, MPO, ITensor}, circuit::Union{Tuple, AbstractVector};
           full_representation::Bool = false, noise = nothing, kwargs...)
```

量子ゲートのリストに対応する回路を、入力ヒルベルト空間 `hilbert` を持つ $n$ 量子ビットのシステム上で実行します。この一般的な関数の特定のメソッドは、キーワード引数 `process` と `noise` によって指定されます。

デフォルトでは（`process = false` および `noise = nothing`）、`runcircuit` は、回路内の各量子ゲートとゼロ積状態との収束に対応する MPS 波動関数を返します。

$$
|\psi\rangle = U_M\dots U_2 U_1|0,0,\dots,0\rangle
$$

`process = true` の場合、出力は完全なユニタリー回路に対応する MPO です：

$$
U = U_M\dots U_2 U_1
$$

`noise` が指定された入力ノイズモデル（遅延表現）に設定されている場合、回路内の各ゲートにクラウス演算子が追加され、出力はノイズのある回路と入力ゼロ状態との収束によって与えられる MPO 密度演算子です：

$$
\rho = \mathcal{E}(|0,\dots,0\rangle\langle0,\dots,0|)
$$

最後に、`noise = ...` と `process = true` の両方が指定されている場合、出力は完全な量子チャネルであり、デフォルトではそのチョイ行列で表現されます：

$$
\Lambda = (1+\mathcal{E})|\Phi\rangle\langle\Phi|^{\otimes n}
$$

`full_representation = true` の場合、収束は近似なしで行われ、出力オブジェクトのサイズは $n$ に対して指数的にスケールします。
