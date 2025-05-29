```
readFullWeights(filename::String)
```

マップの一般化フーリエ変換を計算するために使用されるピクセル重みのセットを読み込みます。

これらの重みは通常事前に計算されており、次のコマンドを使用して[Healpyリポジトリ](https://github.com/healpy/healpy-data)から利用可能なものをダウンロードできます。

```
git clone --depth 1 https://github.com/healpy/healpy-data
```

# 引数:

  * `filename::String`: フルピクセル重みのファイル名

# 戻り値:

  * `Vector{Float64}`: 圧縮されたピクセル重みを含む
