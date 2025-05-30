```
specificity(N::SpeciesInteractionNetwork{<:Partiteness, <:Union{Binary,Quantitative}})
```

決定論的ネットワークの場合、この関数は各最上位種をその特異性にマッピングする辞書を返します。同じインデックス（ペア差指数）がバイナリネットワークと定量的ネットワークの両方に使用されます。値が1は最大の専門性に対応し、値が0は最大の一般性に対応します。このインデックスは対称的であり、値が0.5の種は専門家でも一般家でもありません。

###### 参考文献

[Poisot2012comparative](@citet*)
