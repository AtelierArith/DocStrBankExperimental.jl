```
op(opname::String, s::Index; kwargs...)
```

`opname`という名前の演算子に対応するITensorをIndex `s`のために返します。演算子は、Index `s`のタグの1つに対応する`SiteType`引数を取る`op`または`op!`メソッドのオーバーロードを呼び出すことによって構築され、入力演算子名に対応する`OpName"opname"`引数が含まれます。

演算子名は`"*"`記号を使用して組み合わせることができ、例えば`"S+*S-"`や`"Sz*Sz*Sz"`のようになります。結果は、各演算子を形成し、それらを通常の演算子積または行列乗算に対応する方法で収束させることによって作成されたITensorです。

`op`システムは、演算子名をITensorに変換するためにOpSumシステムによって使用され、MPSに演算子を適用するために直接使用することができます。

# 例

```julia
s = Index(2, "Site,S=1/2")
Sz = op("Sz", s)
```

ITensorに含まれるサイトタイプのために定義されたすべての演算子名は[こちら](https://docs.itensor.org/ITensorMPS/stable/IncludedSiteTypes.html)で確認できます。"S=1/2"や"Qubit"のような一部のサイトタイプは互いのエイリアスであり、演算子定義を共有していることに注意してください。 ```
