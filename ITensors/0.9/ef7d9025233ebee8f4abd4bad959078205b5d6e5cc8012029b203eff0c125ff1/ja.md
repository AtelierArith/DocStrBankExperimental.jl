```
ITensor([::Type{ElT} = Float64, ]::UndefInitializer, inds)
ITensor([::Type{ElT} = Float64, ]::UndefInitializer, inds::Index...)
```

インデックス `inds` と要素型 `ElT` を持つ未定義の要素で満たされた ITensor を構築します。要素型が指定されていない場合、デフォルトは `Float64` です。このコンストラクタを使用する目的の一つは、要素をゼロなどの設定値に初期化するよりも、未定義の方法で初期化する方が速いということです。

ストレージは `NDTensors.Dense` 型になります。

# 例

```julia
i = Index(2,"index_i")
j = Index(4,"index_j")
k = Index(3,"index_k")

A = ITensor(undef,i,j)
B = ITensor(ComplexF64,undef,k,j)
```
