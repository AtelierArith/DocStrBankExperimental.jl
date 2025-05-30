```
VarList_vector(varcollection; components=false, forceview=false) -> VarList_vector
```

`VariableReaction`のコレクションを説明する`VarList_vector`を作成します。次に、`create_accessors`はデータ配列のベクトルを返します。

`components = true`の場合、各ベクトル要素はデータ配列コンポーネントのベクトルになります。

`forceview = true`の場合、各アクセサは型の安定性を助けるために1-Dの`view`になります。これは冗長であっても（つまり、`view`が必要ない場合、v::Vector -> view(v, 1:length(v))）です。
