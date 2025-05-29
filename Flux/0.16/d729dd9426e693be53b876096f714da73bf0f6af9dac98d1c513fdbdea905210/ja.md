```
GroupNorm(channels::Int, G::Int, λ = identity;
          initβ = zeros32,
          initγ = ones32,
          affine = true,
          eps = 1f-5,
          momentum = 0.1f0)
```

[Group Normalization](https://arxiv.org/abs/1803.08494) レイヤー。

`chs` はチャンネルの数で、入力のチャンネル次元を示します。N次元の配列の場合、`N-1` 番目のインデックスがチャンネル次元です。

`G` は統計が計算されるグループの数です。チャンネルの数はグループの数の整数倍でなければなりません。

`channels` はデータのチャンネル次元のサイズである必要があります（下記参照）。

`N > 2` 次元の配列が与えられた場合、`N-1` 番目をチャンネル次元と呼びます。`WHCN` 画像の場合、通常のチャンネル次元です。

`affine=true` の場合、学習可能なチャンネルごとのバイアス `β` とスケール `γ` パラメータを通じて、入力にシフトとリスケールが適用されます。

# 例

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 4, 2);  # 4チャンネルを持つ2つの画像のバッチ

julia> m = GroupNorm(4, 2);

julia> y = m(xs);

julia> isapprox(std(y[:, :, 1:2, 1]), 1, atol=0.1) && std(xs[:, :, 1:2, 1]) != std(y[:, :, 1:2, 1])
true

julia> isapprox(std(y[:, :, 3:4, 2]), 1, atol=0.1) && std(xs[:, :, 3:4, 2]) != std(y[:, :, 3:4, 2])
true
```
