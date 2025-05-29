```
SymplecticAttention
```

シンプレクティックアテンション層を実装します。 [`LinearSymplecticAttention`](@ref)を参照してください。

# キー

以下のキーを保存します：

  * `activation::``AbstractSoftmax`

# コンストラクタ

[`SymplecticAttentionQ`](@ref)および[`SymplecticAttentionP`](@ref)を参照してください。

# 実装

`SymplecticAttention`は、入力ベクトルのシーケンス内のすべてのベクトルのスカラー積を計算する点で、[`MultiHeadAttention`](@ref)や[`VolumePreservingAttention`](@ref)に似ています：

$$
C = Q^TAQ,
$$

ここで、$Q$は入力$Z$の$q$部分です（[`QPT`](@ref）を参照）。行列$A$は、対称または反対称の重み付けを持つことができ（これはキーワード`symmetric::Bool`で調整できます）。

# 拡張ヘルプ

シンプレクティックアテンションメカニズムは、分離可能なハミルトニアンの勾配を計算することによって導出されます。これは[`GSympNet`](@ref)でも行われています。
