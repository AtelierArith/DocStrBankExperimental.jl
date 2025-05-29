```
interpolate(method, points, samples; metric = Euclidean(), returnRBFmatrix = false; smooth = false)
```

`points`で定義された位置でサンプリングされた`samples`のデータの補間を、補間方法`method`に基づいて作成します。`metric`は`Distances`パッケージで定義された任意のメトリックです。重みを解決するために使用されるRBF行列は、ブール値`returnRBFmatrix`で返すことができます。このオプションは、RadialBasisFunction補間にのみ有効です。

`points`は$n×k$の行列である必要があり、$n$はサンプリングされた空間の次元、$k$はポイントの数です。これは、行列の各列が1つのポイントを定義することを意味します。

`samples`は$k×m$の配列であり、$k$はサンプリングされたポイントの数（`points`と同じ）で、$m$はサンプリングされたデータの次元です。

RadialBasisFunction補間は、長さ$k$の補間方法のベクトルを`method`に供給することで、各サンプリングポイントに対してユニークなRBF関数と幅を使用することをサポートしています。

RadialBasisFunction補間は、リッジ回帰を使用してデータポイントの平滑化もサポートしています。すべてのポイントをスカラー値を供給することで均等に平滑化することができます。あるいは、平滑化値のベクトルを供給することで各ポイントを独立して平滑化することもできます。平滑化を使用すると、もはや補間ではないことに注意してください。

返された`ScatteredInterpolant`オブジェクトは、`evaluate`に渡して新しいポイントにデータを補間することができます。
