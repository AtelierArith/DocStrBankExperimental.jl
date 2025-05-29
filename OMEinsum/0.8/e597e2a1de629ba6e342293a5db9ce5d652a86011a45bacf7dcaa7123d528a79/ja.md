```
ein"ij,jk -> ik"(A,B)
```

`numpy.einsum`の表記を理解する文字列マクロインターフェース。文字列を`StaticEinCode`構造体に変換し、`einsum`を評価するために呼び出すことができます。評価順序を制御するには、括弧を使用します。`EinCode`の代わりに、括弧に従って式を評価する`NestedEinsum`が返されます。インデックスラベルの有効な文字範囲は`a-z`および`α-ω`です。

# 例

```jldoctest; setup = :(using OMEinsum)
julia> a, b, c = rand(10,10), rand(10,10), rand(10,1);

julia> ein"ij,jk,kl -> il"(a,b,c) ≈ ein"(ij,jk),kl -> il"(a,b,c) ≈ a * b * c
true
```
