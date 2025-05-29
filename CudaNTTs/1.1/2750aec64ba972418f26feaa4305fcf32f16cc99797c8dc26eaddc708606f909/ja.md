```
ntt!(vec::CuVector{T}, dest::CuVector{T}, plan::NTTPlan{T}, bitreversedoutput::Bool = false) where T<:Union{Int32, Int64, UInt32, UInt64}
```

`vec`の`plan`に従ってNTTを行い、結果を`dest`に格納します。

# 引数:

  * `vec`: NTTのソースベクトル。
  * `dest`: NTTの宛先ベクトル。
  * `plan`: ntt情報を持つNTTPlan。プランを生成するには`plan_ntt()`を参照してください。
  * `bitreversedoutput`: 出力がビット反転順序であるかどうかを決定するBool。デフォルトはfalseです。

`vec`と`dest`が同じで、`bitreversedoutput`がtrueの場合、NTTはインプレースで行われます。ショートカットとして、オーバーロードが提供されています：

```jldoctest
ntt!(vec::CuVector, plan::NTTPlan, bitreversedoutput::Bool = false)
```
