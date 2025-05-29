```
function get_ferrite_grid(
    filename; 
    meshformat=AutomaticMeshFormat(), 
    user_elements=Dict{String,DataType}(), 
    generate_facetsets=true
    )
```

指定された `filename` によってファイルを読み込むことで `Ferrite.Grid` を作成します。

オプション引数:

  * `meshformat`: メッシュが与えられている形式、通常はファイル拡張子によって自動的に検出されます
  * `user_elements`: サポートされていない追加要素を追加するために使用され、別のセルコンストラクタが必要になる場合があります。
  * `generate_facetsets`: すべてのノードセットからフェイスセットを自動的に生成するべきですか？
