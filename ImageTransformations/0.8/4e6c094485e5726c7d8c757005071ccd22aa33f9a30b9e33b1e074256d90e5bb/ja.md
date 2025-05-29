```
invwarpedview(img, tinv, [indices], [degree = Linear()], [fill = NaN]) -> wv
```

`img`のビューを作成し、`wv[I]`に渡された任意のインデックス`I`を`img[inv(tinv)(I)]`に対応させる遅延変換を行います。このアプローチは技術的には逆モードのワーピングとして知られていますが、`InvWarpedView`は前方変換を提供することによって作成されることに注意してください。与えられた変換`tinv`は、`SVector`を入力として受け入れ、`inv(tinv)`をサポートする必要があります。このような多様な変換を作成するための便利なパッケージは[CoordinateTransformations.jl](https://github.com/FugroRoames/CoordinateTransformations.jl)です。

`wv[I]`を呼び出すと、`img`の値は任意の位置`inv(tinv)(I)`で再構築される必要があります。`InvWarpedView`は、補間と外挿を処理する[`WarpedView`](@ref)のラッパーとして機能します。パラメータ`degree`と`fill`は、それぞれbスプラインの次数と外挿スキームを指定するために使用できます。

オプションのパラメータ`indices`は、結果の`wv`のドメインを指定するために使用できます。デフォルトでは、インデックスは`wv`が`img`のすべての元のピクセルを含むように計算されます。
