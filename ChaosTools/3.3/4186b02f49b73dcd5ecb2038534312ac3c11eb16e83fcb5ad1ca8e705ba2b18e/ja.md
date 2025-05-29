```
periodicorbits(ds::DeterministicIteratedMap,
               o, ics [, λs, indss, singss]; kwargs...) -> FP
```

マップ `ds` の順序 `o` の不動点 `FP` を、Schmelcher & Diakonos[^Schmelcher1997] によるアルゴリズムを使用して見つけます。`ics` は進化させる初期条件のコレクション（ベクトルのコンテナ）です。

## オプション引数

オプション引数 `λs, indss, singss` は、適切な値のコンテナでなければなりません。`λs` は数値でも構いません。これらのコンテナの要素は、[`lambdamatrix(λ, inds, sings)`](@ref) に渡され、適切な $\mathbf{\Lambda}_k$ 行列が作成されます。これらの引数が指定されていない場合、`λ=0.001` でランダムな順列が選択されます。

## キーワード引数

  * `maxiters::Int = 100000`: 初期条件が収束していないと主張する前に反復される最大反復回数。
  * `disttol = 1e-10`: 距離の許容誤差。前の状態と次の状態の 2-ノルムが `≤ disttol` の場合、固定点に収束したと見なされます。
  * `inftol = 10.0`: 状態が `norm(state) ≥ inftol` に達した場合、それは無限大に逃げたと見なされ（したがって放棄されます）。
  * `abstol = 1e-8`: 検出された固定点は、以前に検出された点の `abstol` 近傍にある場合は保存されません。距離はユークリッドノルムで測定されます。重複した固定点が得られる場合は、この値を減少させてください。

## 説明

使用されるアルゴリズムは、元のマップ `ds` の不動点を安定なものに変換することによって周期軌道を検出できます。この変換を通じて、

$$
\mathbf{x}_{n+1} = \mathbf{x}_n +
\mathbf{\Lambda}_k\left(f^{(o)}(\mathbf{x}_n) - \mathbf{x}_n\right)
$$

インデックス $k$ は、さまざまな可能な $\mathbf{\Lambda}_k$ をカウントします。

## パフォーマンスノート

*すべての* 初期条件は、*すべての* $\mathbf{\Lambda}_k$ に対して進化され、非常に迅速に長い計算時間につながる可能性があります。

[^Schmelcher1997]: P. Schmelcher & F. K. Diakonos, Phys. Rev. Lett. **78**, pp 4733 (1997)
