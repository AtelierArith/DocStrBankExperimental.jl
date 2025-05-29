```
nodid = addnode!(model,coord)
```

`coord`が`AbstractVector`の`Real`の場合：モデルに単一のノードを追加します。Muscadeは使用する座標系を指定しません。Muscadeは各要素に対してノードの`coord`を処理し、要素のコンストラクタはそれを理解できる必要があります。`nodid`はノード識別子であり、`addelement!`への入力として使用されます。

`coord`が`AbstractMatrix`の場合、その行は座標のベクトルとして扱われます。`nodid`はノード識別子のベクトルとなります。

参照：[`addelement!`](@ref), [`coord`](@ref) , [`describe`](@ref) 
