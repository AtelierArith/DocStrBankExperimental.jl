```
AverageGradient <: DirectionUpdateRule
```

勾配プロセッサに勾配の平均を追加します。以前の方向のセット（内部プロセッサから）と最後の反復が保存され、現在の反復の接線空間にベクトル輸送した後に平均が取られます。

# フィールド

  * `gradients`:               最後の `n` 勾配/方向の更新
  * `last_iterate`:            最後の反復（勾配を輸送するために必要）
  * `direction`:               平均を適用する方向を決定する内部 [`DirectionUpdateRule`](@ref)
  * `vector_transport_method`: 使用するベクトル輸送法

# コンストラクタ

```
AverageGradient(
    M::AbstractManifold,
    p::P=rand(M);
    n::Int=10
    s::DirectionUpdateRule=IdentityUpdateRule();
    gradients = fill(zero_vector(p.M, o.x),n),
    last_iterate = deepcopy(x0),
    vector_transport_method = default_vector_transport_method(M, typeof(p))
)
```

勾配問題に平均を追加します。ここで

  * `n`:                       平均のサイズを決定します
  * `s`:                       保存する勾配を決定する内部 [`DirectionUpdateRule`](@ref)
  * `gradients`:               いくつかの履歴で事前に埋めることができます
  * `last_iterate`:            最後の反復を保存します
  * `vector_transport_method`: 平均を取る前にすべての勾配を現在の反復の接線空間に輸送する方法を決定します
