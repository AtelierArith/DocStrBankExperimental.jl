```
right_virtualspace(ψ::AbstractMPS, [pos=1:length(ψ)])
```

サイト `pos` の右側のボンドのバーチャル空間を返します。

!!! warning
    稀に、バーチャル空間のゲージテンソルが正方形でない場合があり、その結果、`right_virtualspace(ψ, i - 1) == left_virtualspace(ψ, i)` が常に保証されるわけではありません。

