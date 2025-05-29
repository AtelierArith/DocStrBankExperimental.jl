```
rotate(p::PVector, α::Number, β::Number, γ::Number, center::PVector)
```

点 `p` を中心点 `center` の周りでラジアンのオイラー角 (α, β, γ) = (ロール, ピッチ, ヨー) だけ回転させます。角度には単位を持たせることができます。例えば、u"°" (\degree)。
