```
InstanceNorm(channels::Integer, λ=identity;
             initβ=zeros32, initγ=ones32,
             affine=false, track_stats=false,
             eps=1f-5, momentum=0.1f0)
```

[インスタンス正規化](https://arxiv.org/abs/1607.08022)レイヤー。`channels`はデータのチャネル次元のサイズである必要があります（下記参照）。

`N > 2`次元の配列が与えられた場合、`N-1`番目をチャネル次元と呼びます。`WHCN`画像では、通常のチャネル次元です。

`InstanceNorm`は、各`D_1×...×D_{N-2}×1×1`入力スライスの平均と分散を計算し、入力をそれに応じて正規化します。

`affine=true`の場合、学習可能なチャネルごとのバイアス`β`とスケール`γ`パラメータを通じて、入力にシフトと再スケーリングを適用します。

`track_stats=true`の場合、テストフェーズで入力を再正規化するために使用される平均と分散の統計をトレーニングフェーズで蓄積します。

**警告**: `affine`と`track_stats`のデフォルトは、以前のFluxバージョン（< v0.12）では`true`でした。

# 例

```jldoctest
julia> using Statistics

julia> xs = rand(3, 3, 3, 2);  # それぞれ3チャネルを持つ2つの画像のバッチ

julia> m = InstanceNorm(3);

julia> y = m(xs);

julia> isapprox(std(y, dims=1:2), ones(1, 1, 3, 2), atol=0.2) && std(y, dims=1:2) != std(xs, dims=1:2)
true
```
