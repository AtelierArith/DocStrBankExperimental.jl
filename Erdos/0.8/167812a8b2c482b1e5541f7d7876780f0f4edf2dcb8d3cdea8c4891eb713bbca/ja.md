```
struct ConstVertexMap{T} <: AVertexMap{T}
    val::T
end
```

定数ベクトルマップを表す型です。内部の値を変更しようとすると、例えば `vm[1] = 4` のように、静かに失敗します。
