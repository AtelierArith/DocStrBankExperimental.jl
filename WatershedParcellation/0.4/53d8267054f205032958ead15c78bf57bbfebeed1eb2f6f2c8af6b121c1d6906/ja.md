```
 homogeneity_test(px, cov_corr; ks, criteria)
```

`Parcellation`内の`Parcel`を反復処理し、それぞれの均質性をテストします。

オプションで、`ks`という一連のパーセルキーを指定できますが、必ずしも`px`のものとは限りません！ （このアイデアは、この関数への多くの呼び出しで固定されたキーのセットを使用する可能性を許可することです。そして、毎回渡される`Parcellation`は、必ずしもそれらすべてを正確に共有するわけではありません。以下のメソッドを参照してください。これは`Vector{Parcellation{T}}`を受け入れます。）
