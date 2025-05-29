```
CCDData <: AbstractCCDData
CCDData(data::AbstractMatrix, [hdr::FITSHeader])
```

`ImageHDU`を格納するための構造体で、[`AbstractCCDData`](@ref)から派生しています。

`CCDData`は、関連付けられたヘッダーを持つ行列のように機能します。

```julia
ccd = CCDData(zeros(4, 4))

ccd[1]
```

これは、`ccd`に関連付けられた行列の1番目の要素にアクセスします。

```julia
ccd["SIMPLE"]
```

`ccd`からヘッダーに直接アクセスすることもでき、キーは`Symbol`でも構いません。

```julia
ccd[:SIMPLE] = false
```

ヘッダーの値は`ccd`から直接変更できます。

それに対して算術演算を行うこともできます：

```julia
ccd1 = CCDData(zeros(4, 4))
ccd2 = CCDData(ones(4, 4))
sum_ccd1 = ccd1 + ccd2
sum_ccd2 = ccd2 + ccd1
```

`sum_ccd1`は`ccd1`のヘッダーを持ち、`sum_ccd2`は`ccd2`のヘッダーを持っています。

`CCDData`コンストラクタにヘッダーが提供されていない場合、`default_header`が使用されてヘッダーが生成されます。
