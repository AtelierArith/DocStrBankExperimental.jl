```
BatchNorm(channels::Integer, λ=identity;
          initβ=zeros32, initγ=ones32,
          affine=true, track_stats=true, active=nothing,
          eps=1f-5, momentum= 0.1f0)
```

[バッチ正規化](https://arxiv.org/abs/1502.03167) レイヤー。`channels` はデータのチャネル次元のサイズである必要があります（以下を参照）。

`N` 次元の配列が与えられた場合、`N-1` 番目をチャネル次元と呼びます。特徴ベクトルのバッチの場合、これは単にデータ次元ですが、`WHCN` 画像の場合は通常のチャネル次元です。

`BatchNorm` は、各 `D_1×...×D_{N-2}×1×D_N` 入力スライスの平均と分散を計算し、入力をそれに応じて正規化します。

`affine=true` の場合、学習可能なチャネルごとのバイアス β とスケール γ パラメータを通じて、入力にシフトと再スケーリングを適用します。

正規化の後、要素ごとの活性化 `λ` が適用されます。

`track_stats=true` の場合、トレーニングフェーズで平均と分散の統計を蓄積し、テストフェーズで入力を再正規化するために使用されます。

推論中は [`testmode!`](@ref) を使用してください。

# 例

```julia-repl
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # 3 チャネルを持つ 2 つの画像のバッチ

julia> m = BatchNorm(3);

julia> Flux.trainmode!(m);

julia> isapprox(std(m(xs)), 1, atol=0.1) && std(xs) != std(m(xs))
true
```
