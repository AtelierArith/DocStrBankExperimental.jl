# 拡張ヘルプ

```
translate(H::Hyperplane, v::AbstractVector; share::Bool=false)
```

### 注意事項

ハイパープレーンの法線ベクトル（ベクトル $a$ は $a⋅x = b$ の中で）は、`share == true` の場合、元のハイパープレーンと共有されます。

### アルゴリズム

ハイパープレーン $a⋅x = b$ は、ハイパープレーン $a⋅x = b + a⋅v$ に変換されます。言い換えれば、ドット積 $a⋅v$ を $b$ に加えます。
