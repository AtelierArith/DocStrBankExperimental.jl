```
left_virtualspace(ψ::AbstractMPS, [pos=1:length(ψ)])
```

サイト `pos` の左側のボンドのバーチャルスペースを返します。

!!! warning
    稀に、バーチャルスペース上のゲージテンソルが正方形でない場合があり、その結果、`right_virtualspace(ψ, i - 1) == left_virtualspace(ψ, i)` が常に保証されるわけではありません。

