```
register(forward::Function, backward::Function; multiple::Bool=false)
```

関数 `forward` を逆伝播勾配ルール `backward` に登録します。  ∘ `forward`: $n$ 入力を受け取り、$m$ テンソルを出力します。 $m>1$ の場合、キーワード `multiple` は true でなければなりません。  ∘ `backward`: `forward` の float/double 出力テンソルから $\tilde m$ のトップ勾配、`forward` の $m$ 出力、および `forward` の $n$ 入力を受け取ります。 `backward` は `forward` の各入力に対して $n$ 勾配を出力します。 `forward` の入力 $i$ が float/double でない場合、`backward` は対応する勾配に対して `nothing` を返すべきです。

# 例

```julia
forward = x->log(1+exp(x))
backward = (dy, y, x)->dy*(1-1/(1+y))
f = register(forward, backward)
```
