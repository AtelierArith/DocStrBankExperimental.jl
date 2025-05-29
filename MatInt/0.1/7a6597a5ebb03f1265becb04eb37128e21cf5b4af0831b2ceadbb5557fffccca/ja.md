このパッケージは、整数行列のスミス標準形とエルミート標準形、アーベル群の生成元の集合に対するダイアコニス-グラハム標準形、および整数行列を格子として扱うためのいくつかの関数を提供します。

コードの大部分は、A. Storjohann、R. Wainwright、F. Gähler、D. Holtによって作成された`GAP4`から移植されています。`NormalFormIntMat`のコードは、元のものと同様に読みづらいです。ダイアコニス-グラハム標準形は`GAP3/Chevie`から移植されています。

結果の有効性を確保する最良の方法は、オーバーフローが発生した場合にエラーを返す`SaferIntegers`の行列を使用することです。エラーが発生した場合は、より広い型で計算をやり直してください。

APIについては、`smith, smith_transforms, hermite, hermite_transforms, col_hermite, col_hermite_transforms, diaconis_graham, baseInt, complementInt, lnullspaceInt, solutionmatInt, intersect_rowspaceInt`のドキュメント文字列を参照してください。

*単位行列*とは、可逆であり、その逆行列も整数行列である整数行列を意味します。
