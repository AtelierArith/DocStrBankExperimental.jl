```
opening!(dst, wrk, A, B=3; order=FORWARD_FILTER, slow=false) -> dst
```

は、`wrk`を作業配列として使用して、構造要素`B`によって`A`のオープニングの結果で`dst`を上書きします。引数`dst`、`wrk`、および`A`は類似の配列でなければならず、`dst`と`A`は同一であってもよいですが、`wrk`は`A`または`dst`と同じ配列であってはなりません。宛先`dst`が返されます。

この種のフィルタの説明や引数およびキーワードの意味については、[`opening`](@ref)を参照してください。
