```
intt!(vec::CuVector{T}, dest::CuVector{T}, plan::INTTPlan{T}, bitreversedinput::Bool = false) where T<:Union{Int32, Int64, UInt32, UInt64}
```

`vec`の`plan`に従ってINTTを行い、結果を`dest`に格納します。

# 引数:

  * `vec`: INTTのソースベクトル。
  * `dest`: INTTの宛先ベクトル。
  * `plan`: INTT情報を持つINTTPlan。プランを生成するには`plan_ntt()`を参照してください。
  * `bitreversedinput`: 入力がビット反転順であるかどうかを決定するBool。デフォルトはfalseです。

`vec`と`dest`が同じで、`bitreversedoutput`がtrueの場合、INTTはインプレースで行われます。ショートカットとして、オーバーロードが提供されています：

```jldoctest
intt!(vec::CuVector, plan::INTTPlan, bitreversedinput::Bool = false)
```
