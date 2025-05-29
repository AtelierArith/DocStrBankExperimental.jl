`VirtualBrownianTree`は、初期時刻`t0`、プロセスの最初の値`W0`、および（オプションで）補助擬似プロセスの最初の値`Z0`からノイズプロセスを構築します。コンストラクタは次のように定義されています。

```julia
VirtualBrownianTree(t0,
    W0,
    Z0 = nothing,
    dist = WHITE_NOISE_DIST,
    bridge = VBT_BRIDGE;
    kwargs...)
```

ここで、`dist`は、最終時刻`tend`のノイズプロセスの終点`Wend`（`Zend`）を生成するために使用される分布を指定します。`bridge`は、使用されるブラウンianブリッジの分布を示します。デフォルトでは`tend`は`t0+1`に固定されていますが、カスタム`tend`をキーワード引数として渡すことで変更できます。以下のキーワード引数が利用可能です。

  * `tend`はノイズプロセスの終了時刻です。
  * `Wend`はノイズプロセスの終了値です。
  * `Zend`は擬似ノイズプロセスの終了値です。
  * `atol`は再帰が終了する際の絶対許容誤差を表します。
  * `tree_depth`は、シミュレーションの再帰ステップを減らすことで速度を向上させるために、シード、ノイズ値、および時刻のキャッシュを保存することを可能にします。
  * `search_depth`は、`atol`が達成されない場合のツリーの最大検索深度です。
  * `rng`は、乱数を生成するために使用される分割可能なPRNGです。デフォルト：Random123パッケージの`Threefry4x()`。

## VirtualBrownianTreeの例

この例では、メモリ消費を最小限に抑えるために、最小の`tree_depth=0`を持つ`VirtualBrownianTree`に基づいて多次元ブラウンianプロセスを定義します。

```julia
W0 = zeros(10)
W = VirtualBrownianTree(0.0, W0; tree_depth = 0)

prob = NoiseProblem(W, (0.0, 1.0))
sol = solve(prob; dt = 1 / 10)
```

`tree_depth`を増やしてルックアップキャッシュを使用することで、実行時間を大幅に短縮できます。したがって、`VirtualBrownianTree`は、メモリと速度のトレードオフを簡単に行うことを可能にします。
