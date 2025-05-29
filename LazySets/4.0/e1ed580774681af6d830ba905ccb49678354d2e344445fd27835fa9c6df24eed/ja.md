```
sample(X::LazySet{N}, num_samples::Int;
       [sampler]=_default_sampler(X),
       [rng]::AbstractRNG=GLOBAL_RNG,
       [seed]::Union{Int, Nothing}=nothing,
       [include_vertices]=false,
       [VN]=Vector{N}) where {N}
```

任意の集合 `X` のランダムサンプリング。

### 入力

  * `X`           – サンプリングされる集合
  * `num_samples` – ランダムサンプルの数
  * `sampler`     – （オプション、デフォルト: `_default_sampler(X)`）使用されるサンプラー;                  [`CombinedSampler`](@ref) にフォールバックします
  * `rng`         – （オプション、デフォルト: `GLOBAL_RNG`）乱数生成器
  * `seed`        – （オプション、デフォルト: `nothing`）再シード用のシード
  * `include_vertices` – （オプション、デフォルト: `false`）`X` の頂点を含めるオプション
  * `VN`          – （オプション、デフォルト: `Vector{N}`）サンプリングされた点のベクトルタイプ

### 出力

`num_samples` ベクトルのベクトル。`num_samples` が渡されない場合、結果は単一のサンプル（ベクトルにラップされていない）です。

### アルゴリズム

それぞれの `Sampler` のドキュメントを参照してください。

### 注意事項

`include_vertices == true` の場合、`vertices` で計算されたすべての頂点を含めます。あるいは、数 $k$ が渡された場合、`vertices(X)` によって返された最初の $k$ 頂点をプロットします。
