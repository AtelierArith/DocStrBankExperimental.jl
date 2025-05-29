```
general_mixed_increment!(material::AbstractMaterial,
                         dstrain_knowns::AbstractVector{<:Union{T, Missing}},
                         dstress_knowns::AbstractVector{<:Union{T, Missing}},
                         dt::Real,
                         dstrain::AbstractVector{<:Union{T, Missing}}=dstrain_knowns,
                         max_iter::Integer=50, norm_acc::T=1e-9) where T <: Real
```

`material`に対して互換性のあるひずみ増分を見つけます。これは、いくつかの成分がひずみ駆動であり、いくつかが応力駆動であるような、二軸の「蝶ネクタイ」および「逆蝶ネクタイ」荷重を許可する`general_increment!`と`stress_driven_general_increment!`の組み合わせです：

```
Corona, E., Hassan, T. and Kyriakides, S. (1996) On the Performance of
Kinematic Hardening Rules in Predicting a Class of Biaxial Ratcheting
Histories. International Journal of Plasticity, Vol 12, pp. 117--145.
```

また、以下も参照してください：

```
Bari, Shafiqul. (2001) Constitutive modeling for cyclic plasticity and ratcheting.
Ph.D. thesis, North Carolina State University.
```

これは、これらの荷重の下でのいくつかの異なる塑性モデルの応答を比較しています。

各既知の成分は、ひずみ駆動または応力駆動のいずれかでなければなりません。両方ではありません。

dstrainとdstressの既知の成分の組み合わせは、有効な材料状態を記述しなければなりません。そうでない場合、最適化アルゴリズムが収束しないか、意味のない解を返す可能性があります。
