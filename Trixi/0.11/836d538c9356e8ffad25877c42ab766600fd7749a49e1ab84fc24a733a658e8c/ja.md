```
T8codeMesh{NDIMS, RealT}(forest, boundary_names; polydeg = 1, mapping = nothing)
```

`T8codeMesh`のメインメッシュコンストラクタで、指定されたt8code `forest`オブジェクトをラップします。このコンストラクタは通常、他の`T8codeMesh`コンストラクタによって呼び出されます。

# 引数

  * `forest`: t8codeフォレストへのポインタ。
  * `boundary_names`: 境界名のリスト。
  * `polydeg::Integer`: メッシュのジオメトリを格納するために使用される多項式の次数。                     マッピングは、各ツリーの指定された次数の補間多項式によって近似されます。
  * `mapping`: インポートされたメッシュを物理ドメインに変換するマッピングを記述する`NDIMS`変数の関数。アイデンティティマップには`nothing`を使用します。
