```
warpedview(img, tform, [indices], [degree = Linear()], [fill = NaN]) -> wv
```

`img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を`img[tform(I)]`に対応させる遅延変換を行います。このアプローチは逆モードワーピングとして知られています。与えられた変換`tform`は、`SVector`を入力として受け入れる必要があります。さまざまな変換を作成するための便利なパッケージは、[CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl)です。

`wv[I]`を呼び出すとき、`img`の値は、ピクセルの格子上にない任意の位置`tform(I)`で再構築される必要があります。この再構築の方法は、`img`のタイプとオプションのパラメータ`degree`によって異なります。`img`が通常の配列である場合、オン-grid bスプライン補間が使用され、`img`のピクセルが係数として機能します。使用するbスプラインの次数は、パラメータ`degree`で設定できます。2つの可能な値は、線形補間のための`degree = Linear()`、または最近傍補間のための`degree = Constant()`です。

`tform(I)`が`img`のドメインの外部にマッピングされる場合、その位置は値`fill`に設定されます（要素タイプがサポートしている場合はデフォルトで`NaN`、そうでない場合は`0`）。さらに、パラメータ`fill`は、`Flat()`、`Periodic()`、または`Reflect()`などの外挿スキームも受け入れます。

オプションのパラメータ`indices`は、結果の`WarpedView`のドメインを指定するために使用できます。デフォルトでは、インデックスは、結果の`WarpedView`が`img`のすべての元のピクセルを含むように計算されます。これを行うには、`inv(tform)`を計算する必要があります。与えられた変換`tform`が`inv`をサポートしていない場合、パラメータ`indices`を手動で指定する必要があります。

`warpedview`は本質的に、[`warp`](@ref)の非コピー、遅延バージョンです。そのため、2つの関数は同じインターフェースを共有しますが、1つの重要な違いがあります。`warpedview`は、結果の`WarpedView`が`img`のビューであることを主張します（すなわち、`parent(warpedview(img, ...)) === img`）。したがって、`warpedview`はパラメータ`degree`を`Linear()`または`Constant()`のいずれかに制限します。
