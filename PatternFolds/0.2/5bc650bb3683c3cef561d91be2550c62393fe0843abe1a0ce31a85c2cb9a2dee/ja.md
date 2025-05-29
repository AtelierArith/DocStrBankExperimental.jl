```
VectorFold{T,V <: AbstractVector{T}}
```

折りたたみベクトルのための可変構造体で、AbstractVectorのメソッドを拡張します。`IVectorFold`と比較して、この構造体はイテレータを使用することで約20%速くなります。この構造体は、`current` *未展開* パターンへのアクティブポインタを保持していることに注意してください。しかし、その外部の動作は`IVectorFold`に似ています。
