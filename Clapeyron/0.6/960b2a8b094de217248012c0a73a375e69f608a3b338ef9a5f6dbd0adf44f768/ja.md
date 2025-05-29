```
epsilon_LorentzBerthelot(ϵ::SingleOrPair,k::PairParam)::PairParam
epsilon_LorentzBerthelot(ϵ::SingleOrPair)::PairParam
```

単一またはペアパラメータの組み合わせルール。非対角成分が次のように等しいペアパラメータを返します：

```
ϵᵢⱼ = (1 - kᵢⱼ)*√(ϵᵢϵⱼ)
```

`kᵢⱼ`が定義されていない場合、定義は単純な幾何平均に簡略化されます：

```
ϵᵢⱼ = √(ϵᵢϵⱼ)
```

すでに設定されている非対角成分は無視されます。

単一パラメータが入力として渡された場合、それはペアパラメータに変換され、`ϵᵢᵢ = ϵᵢ`となります。
