```
MomentumGradient <: DirectionUpdateRule
```

勾配プロセッサにモーメンタムを追加し、最後の方向と最後の反復を保存し、新しいものは $η_i = m*η_{i-1}' - s d_i$ として構成されます。ここで、$sd_i$ は現在の（内部の）方向であり、$η_{i-1}'$ はモーメンタム $m$ で乗算された最後の方向を輸送したベクトルです。

# フィールド

  * `p_old`:                   (`rand(M)`) 最後の方向を平行輸送するための最後の反復を記憶します
  * `momentum`:                (`0.2`) モーメンタムの係数
  * `direction`:               モーメンタムを追加する方向を決定する内部 [`DirectionUpdateRule`](@ref)
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) 使用するベクトル輸送法
  * `X_old`:                   (`zero_vector(M,x0)`) モーメンタムとして追加された最後の勾配/方向更新

# コンストラクタ

勾配問題にモーメンタムを追加します。デフォルトでは、勾配評価のみが使用されます。

```
MomentumGradient(
    M::AbstractManifold;
    p=rand(M),
    s::DirectionUpdateRule=IdentityUpdateRule();
    X=zero_vector(p.M, x0), momentum=0.2
    vector_transport_method=default_vector_transport_method(M, typeof(p)),
)
```

モーメンタム勾配ルールを `s` に初期化し、`p` と `X` は中間値のメモリです。
