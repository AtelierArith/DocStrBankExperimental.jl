```
I = imagesc(mat; x=, y=, hdr=, proj4=, wkt=, clim=, cmap=, GI=, kw...)
```

imagescはFloat行列またはGMTgridタイプを受け取り、デフォルトで[0, 255]の範囲にスケーリングします。このプロセスでGMTimageタイプを作成します。これらのタイプは座標や投影情報を考慮できるため、オプション引数があります。Matlabの仲間とは異なり、結果を表示するのではなく（`imshow(mat)`で簡単に行えます）、代わりにGMTimageオブジェクトを返します。

### Kwargs

  * `clim`: cmin cmaxの形式の2要素ベクトルとしてclimsを指定します。スケーリングされた画像の値がcmin以下の場合、その値が割り当てられます。cmaxについても同様です。
  * `cmap`: 提供される場合、`cmap`はGMTcptであり、その内容は`GMTimage`カラーマップに変換されます。
  * `GI`: これはGMTgridまたはGMTimageのいずれかであり、その内容は作成された画像結果に添付できる空間内容（x,y座標）および投影情報を設定するために使用されます。これは`x=, y=, proj4=...`オプションの便利な代替手段です。
  * `stretch`: このオプションは、`z`値の範囲の間隔を選択し、それらのみを使用して[0 255]の範囲にスケーリングするために示されています。`stretch=true`は、`histogram`への呼び出しを介してヒストグラムストレッチングの良い値を自動的に決定します。`stretch=(zmin,zmax)`の形式は、入力制限を直接指定することを可能にします。$histogram(mat, show=true)$の以前のプロットは良い値を決定するのに役立ちます。このオプション`stretch`が使用されると、他のすべてのオプションは無視されることに注意してください。$rescale$関数も参照してください。
  * `region:` `region`で指定されたグリッドの領域にアクションを制限します。このキーワードに関する拡張ドキュメントについては、$coast$マニュアルを参照してください。このオプションは、`mat`がGMTgridタイプの場合にのみ利用可能です。

もし'mat'がUInt16 GMTimageタイプである場合、エラーを発生させる代わりに`rescale(I, stretch=true, type=UInt8)`を呼び出します。この場合、`clim`は希望するストレッチ範囲を指定するための2要素ベクトルであることができます。デフォルトは`histogram`にこれらの値を推測させることです。
